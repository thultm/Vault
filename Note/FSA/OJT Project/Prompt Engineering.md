# 1. Guidelines 
- Principle 1: Write clear and specific instructions
- Principle 2: Give the model time to “think”
### Principle 1 
#### Tactic 1: Use delimiters to clearly indicate distinct parts of the input
- Delimiters can be anything like: ***\`\`\`, """, < >, \<tag\> \</tag\>, :***
```python
text = f"""
You should express what you want a model to do by \ 
providing instructions that are as clear and \ 
specific as you can possibly make them. \ 
This will guide the model towards the desired output, \ 
and reduce the chances of receiving irrelevant \ 
or incorrect responses. Don't confuse writing a \ 
clear prompt with writing a short prompt. \ 
In many cases, longer prompts provide more clarity \ 
and context for the model, which can lead to \ 
more detailed and relevant outputs.
"""
prompt = f"""
Summarize the text delimited by triple backticks \ 
into a single sentence.
\```{text}\```
"""
response = get_completion(prompt)
```
#### Tactic 2: Ask for a structured output
- JSON, HTML 
	```python
	prompt = f"""
	Generate a list of three made-up book titles along \ 
	with their authors and genres. 
	Provide them in JSON format with the following keys: 
	book_id, title, author, genre.
	"""
	```
#### Tactic 3: Ask the model to check whether conditions are satisfied
```python
text_1 = f"""
Making a cup of tea is easy! First, you need to get some \ 
water boiling. While that's happening, \ 
grab a cup and put a tea bag in it. Once the water is \ 
hot enough, just pour it over the tea bag. \ 
Let it sit for a bit so the tea can steep. After a \ 
few minutes, take out the tea bag. If you \ 
like, you can add some sugar or milk to taste. \ 
And that's it! You've got yourself a delicious \ 
cup of tea to enjoy.
"""
prompt = f"""
You will be provided with text delimited by triple quotes. 
If it contains a sequence of instructions, \ 
re-write those instructions in the following format:

Step 1 - ...
Step 2 - …
…
Step N - …

If the text does not contain a sequence of instructions, \ 
then simply write \"No steps provided.\"

\"\"\"{text_1}\"\"\"
"""
response = get_completion(prompt)
print("Completion for Text 1:")
print(response)
```
#### Tactic 4: "Few-shot" prompting
```python
prompt = f"""
Your task is to answer in a consistent style.

<child>: Teach me about patience.

<grandparent>: The river that carves the deepest \ 
valley flows from a modest spring; the \ 
grandest symphony originates from a single note; \ 
the most intricate tapestry begins with a solitary thread.

<child>: Teach me about resilience.
"""
response = get_completion(prompt)
print(response)
```
### Principle 2
#### Tactic 1: Specify the steps required to complete a task
```python
text = f"""
In a charming village, siblings Jack and Jill set out on \ 
a quest to fetch water from a hilltop \ 
well. As they climbed, singing joyfully, misfortune \ 
struck—Jack tripped on a stone and tumbled \ 
down the hill, with Jill following suit. \ 
Though slightly battered, the pair returned home to \ 
comforting embraces. Despite the mishap, \ 
their adventurous spirits remained undimmed, and they \ 
continued exploring with delight.
"""
# example 1
prompt_1 = f"""
Perform the following actions: 
1 - Summarize the following text delimited by triple \
backticks with 1 sentence.
2 - Translate the summary into French.
3 - List each name in the French summary.
4 - Output a json object that contains the following \
keys: french_summary, num_names.

Separate your answers with line breaks.

Text:
\```{text}\```
"""
response = get_completion(prompt_1)
print("Completion for prompt 1:")
print(response)
```
#### Tactic 2: Ask for output in a specified format
```python
prompt_2 = f"""
Your task is to perform the following actions: 
1 - Summarize the following text delimited by 
  <> with 1 sentence.
2 - Translate the summary into French.
3 - List each name in the French summary.
4 - Output a json object that contains the 
  following keys: french_summary, num_names.

Use the following format:
Text: <text to summarize>
Summary: <summary>
Translation: <summary translation>
Names: <list of names in summary>
Output JSON: <json with summary and num_names>

Text: <{text}>
"""
response = get_completion(prompt_2)
print("\nCompletion for prompt 2:")
print(response)
```
#### Tactic 3: Instruct the model to work out its own solution before rushing to a conclusion
```python
prompt = f"""
Determine if the student's solution is correct or not.

Question:
I'm building a solar power installation and I need \
 help working out the financials. 
- Land costs $100 / square foot
- I can buy solar panels for $250 / square foot
- I negotiated a contract for maintenance that will cost \ 
me a flat $100k per year, and an additional $10 / square \
foot
What is the total cost for the first year of operations 
as a function of the number of square feet.

Student's Solution:
Let x be the size of the installation in square feet.
Costs:
1. Land cost: 100x
2. Solar panel cost: 250x
3. Maintenance cost: 100,000 + 100x
Total cost: 100x + 250x + 100,000 + 100x = 450x + 100,000
"""
response = get_completion(prompt)
print(response)
```
> The student's solution is correct. The total cost for the first year of operations as a function of the number of square feet is indeed 450x + 100,000.
 
 Note that the student's solution is actually not correct.
 We can fix this by instructing the model to work out its own solution first.

```python 
 prompt = f"""
Your task is to determine if the student's solution \
is correct or not.
To solve the problem do the following:
- First, work out your own solution to the problem including the final total. 
- Then compare your solution to the student's solution \ 
and evaluate if the student's solution is correct or not. 
Don't decide if the student's solution is correct until 
you have done the problem yourself.

Use the following format:
Question:
\```
question here
\```
Student's solution:
\```
student's solution here
\```
Actual solution:
\```
steps to work out the solution and your solution here
\```
Is the student's solution the same as actual solution \
just calculated:
\```
yes or no
\```
Student grade:
\```
correct or incorrect
\```

Question:
\```
I'm building a solar power installation and I need help \
working out the financials. 
- Land costs $100 / square foot
- I can buy solar panels for $250 / square foot
- I negotiated a contract for maintenance that will cost \
me a flat $100k per year, and an additional $10 / square \
foot
What is the total cost for the first year of operations \
as a function of the number of square feet.
\``` 
Student's solution:
\```
Let x be the size of the installation in square feet.
Costs:
1. Land cost: 100x
2. Solar panel cost: 250x
3. Maintenance cost: 100,000 + 100x
Total cost: 100x + 250x + 100,000 + 100x = 450x + 100,000
\```
Actual solution:
"""
response = get_completion(prompt)
print(response)
```
## Model Limitations: Hallucinations
- Hallucinations: Makes statements that sound plausible but are not true.
  - Reducing hallucinations: First find relevant information, then answer the question based on the relevant information.
# 2. Iterative Prompt Development
![](https://i.imgur.com/RQKFUBG.png)
## Generate a marketing product description from a product fact sheet
```python
fact_sheet_chair = """

OVERVIEW

- Part of a beautiful family of mid-century inspired office furniture, 

including filing cabinets, desks, bookcases, meeting tables, and more.

- Several options of shell color and base finishes.

- Available with plastic back and front upholstery (SWC-100) 

or full upholstery (SWC-110) in 10 fabric and 6 leather options.

- Base finish options are: stainless steel, matte black, 

gloss white, or chrome.

- Chair is available with or without armrests.

- Suitable for home or business settings.

- Qualified for contract use.

​

CONSTRUCTION

- 5-wheel plastic coated aluminum base.

- Pneumatic chair adjust for easy raise/lower action.

​

DIMENSIONS

- WIDTH 53 CM | 20.87”

- DEPTH 51 CM | 20.08”

- HEIGHT 80 CM | 31.50”

- SEAT HEIGHT 44 CM | 17.32”

- SEAT DEPTH 41 CM | 16.14”

​

OPTIONS

- Soft or hard-floor caster options.

- Two choices of seat foam densities: 

 medium (1.8 lb/ft3) or high (2.8 lb/ft3)

- Armless or 8 position PU armrests 

​

MATERIALS

SHELL BASE GLIDER

- Cast Aluminum with modified nylon PA6/PA66 coating.

- Shell thickness: 10 mm.

SEAT

- HD36 foam

​

COUNTRY OF ORIGIN

- Italy

"""
```

```python
prompt = f"""
Your task is to help a marketing team create a 
description for a retail website of a product based 
on a technical fact sheet.

Write a product description based on the information 
provided in the technical specifications delimited by 
triple backticks.

Technical specifications: \```{fact_sheet_chair}\```
"""
response = get_completion(prompt)
print(response)
```
> Introducing the SWC-100/SWC-110 Office Chair, a sleek and stylish addition to any workspace. This chair is part of a stunning collection of mid-century inspired office furniture, offering a cohesive look with filing cabinets, desks, bookcases, meeting tables, and more.
> 
> Customize your chair with several options for shell color and base finishes to suit your personal style. Choose between plastic back and front upholstery or full upholstery in a variety of fabric and leather options. The base finish options include stainless steel, matte black, gloss white, or chrome, allowing you to create the perfect look for your space.
> 
> Designed for both home and business settings, this chair is suitable for contract use and offers comfort and functionality. The 5-wheel plastic coated aluminum base provides stability, while the pneumatic chair adjust allows for easy raise/lower action.
> 
> With dimensions of 53 cm in width, 51 cm in depth, and 80 cm in height, this chair offers a comfortable seat height of 44 cm and seat depth of 41 cm. Choose between soft or hard-floor caster options and two seat foam densities for personalized comfort.
> 
> Constructed with high-quality materials, including a cast aluminum shell with modified nylon coating and HD36 foam seat, this chair is built to last. Made in Italy, this chair combines style, comfort, and durability for a premium seating experience.
> 
> Upgrade your workspace with the SWC-100/SWC-110 Office Chair and elevate your office aesthetic with this modern and functional piece of furniture.
## Issue 1: The text is too long
- Limit the number of words/sentences/characters.
	```python
	prompt = f"""
	Your task is to help a marketing team create a 
	description for a retail website of a product based 
	on a technical fact sheet.
	
	Write a product description based on the information 
	provided in the technical specifications delimited by 
	triple backticks.
	
	Use at most 50 words.
	
	Technical specifications: \```{fact_sheet_chair}\```
	"""
	response = get_completion(prompt)
	print(response)
	
	```
> Introducing our versatile and stylish office chair, part of a mid-century inspired furniture collection. Choose from a variety of colors, finishes, and upholstery options to suit your space. With a durable construction and adjustable features, this chair is perfect for both home and business use. Made in Italy.
## Issue 2. Text focuses on the wrong details
- Ask it to focus on the aspects that are relevant to the intended audience.
	```python
	prompt = f"""
	Your task is to help a marketing team create a 
	description for a retail website of a product based 
	on a technical fact sheet.
	
	Write a product description based on the information 
	provided in the technical specifications delimited by 
	triple backticks.
	
	The description is intended for furniture retailers, 
	so should be technical in nature and focus on the 
	materials the product is constructed from.
	
	Use at most 50 words.
	
	Technical specifications: \```{fact_sheet_chair}\```
	"""
	response = get_completion(prompt)
	print(response)
	```
> Introducing our versatile and stylish office chair, part of a mid-century inspired furniture collection. Constructed with a durable cast aluminum shell and base glider coated with modified nylon PA6/PA66. The seat features high-density HD36 foam for comfort. Available in various colors and finishes, suitable for both home and business use. Made in Italy.

```python
prompt = f"""
Your task is to help a marketing team create a 
description for a retail website of a product based 
on a technical fact sheet.

Write a product description based on the information 
provided in the technical specifications delimited by 
triple backticks.

The description is intended for furniture retailers, 
so should be technical in nature and focus on the 
materials the product is constructed from.

At the end of the description, include every 7-character 
Product ID in the technical specification.

Use at most 50 words.

Technical specifications: \```{fact_sheet_chair}\```
"""
response = get_completion(prompt)
print(response)
```
> Introducing our versatile office chair, crafted with a durable cast aluminum shell and base glider coated with modified nylon. The seat features high-density foam for comfort and support. Choose from a variety of finishes and upholstery options to suit your style. Perfect for home or office use. 
> 
> Product IDs: SWC-100, SWC-110

## Issue 3. Description needs a table of dimensions
- Ask it to extract information and organize it in a table.
```python
	prompt = f"""
	Your task is to help a marketing team create a 
	description for a retail website of a product based 
	on a technical fact sheet.
	
	Write a product description based on the information 
	provided in the technical specifications delimited by 
	triple backticks.
	
	The description is intended for furniture retailers, 
	so should be technical in nature and focus on the 
	materials the product is constructed from.
	
	At the end of the description, include every 7-character 
	Product ID in the technical specification.
	
	After the description, include a table that gives the 
	product's dimensions. The table should have two columns.
	In the first column include the name of the dimension. 
	In the second column include the measurements in inches only.
	
	Give the table the title 'Product Dimensions'.
	
	Format everything as HTML that can be used in a website. 
	Place the description in a <div> element.
	
	Technical specifications: \```{fact_sheet_chair}\```
	"""
	
	response = get_completion(prompt)
	print(response)
```
<div>
<p>This mid-century inspired office chair is a stylish and functional addition to any workspace. The chair is available in a variety of shell colors and base finishes to suit your aesthetic preferences. Choose between plastic back and front upholstery or full upholstery in a range of fabric and leather options. The chair features a 5-wheel plastic coated aluminum base for stability and mobility, along with a pneumatic adjustment for easy height customization. Whether for home or business use, this chair is designed to provide comfort and support. Made with high-quality materials, including cast aluminum with a modified nylon coating for the shell and HD36 foam for the seat, this chair is built to last. Enhance your office with this versatile and durable seating option.</p>

<p>Product IDs: SWC-100, SWC-110</p>
</div>

<table>
  <caption>Product Dimensions</caption>
  <tr>
    <th>Dimension</th>
    <th>Measurements (inches)</th>
  </tr>
  <tr>
    <td>Width</td>
    <td>20.87"</td>
  </tr>
  <tr>
    <td>Depth</td>
    <td>20.08"</td>
  </tr>
  <tr>
    <td>Height</td>
    <td>31.50"</td>
  </tr>
  <tr>
    <td>Seat Height</td>
    <td>17.32"</td>
  </tr>
  <tr>
    <td>Seat Depth</td>
    <td>16.14"</td>
  </tr>
</table>
# 3. Summarizing 
