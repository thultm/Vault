# I. Docker
## 1. Thành phần của Docker
- **Docker Engine**: dùng để tạo ra Docker image và chạy Docker container.
- **Docker Hub**: dịch vụ lưu trữ giúp chứa các Docker image.
- **Docker Machine**: tạo ra các Docker engine trên máy chủ.
- **Docker Compose**: chạy ứng dụng bằng cách định nghĩa cấu hình các Docker container thông qua tệp cấu hình
- **[[#3. Docker image|Docker image]]**: một dạng tập hợp các tệp của ứng dụng, được tạo ra bởi Docker engine. Nội dung của các Docker image sẽ không bị thay đổi khi di chuyển. Docker image được dùng để chạy các Docker container.
- **[[#4. Docker container|Docker container]]**: một dạng runtime của các Docker image, dùng để làm môi trường chạy ứng dụng.
## 2. DockerFile
> Là một tệp chứa một tập hợp các hướng dẫn mô tả cấu hình môi trường. Nó như một script dùng để build các image trong container. 
- Bao gồm các câu lệnh liên tiếp nhau được thực hiện tự động trên một image gốc để tạo ra một image mới. 
- Giúp đơn giản hóa tiến trình từ lúc bắt đầu đến khi kết thúc. 
- Quy định Docker image được khởi tạo từ đâu, gồm những gì trong đó. 
- Ta build Dockerfile để tạo ra docker image (docker image thường có dung lượng nhỏ từ vài MB đến lớn vài GB).
### 2.1 Cấu hình một file [[#2. DockerFile|DockerFile]]
- Một [[#2. DockerFile|DockerFile]] phải bắt đầu bằng chỉ thị **FROM** để khai báo parent image nào sẽ được sử dụng để làm nền tảng xây dựng image của riêng bạn.
- **FROM**: Dùng để chỉ ra image được build từ đâu (từ image gốc nào), chỉ thị này phải được đặt trên cùng của [[#2. DockerFile|DockerFile]]. Ví dụ: 
```DockerFile
FROM ubuntu:16.04
```
- **MAINTAINER**: Chỉ thị này là tùy chọn. Nó dùng để khai báo thông tin của tác giả xây dựng lên images. Ví dụ:
```Dockerfile
MAINTAINER NguyenNgoc <nguyenngoc.hust.97@gmail.com>
```
- **RUN**: Chỉ thị này dùng để thực thi một số câu lệnh trong quá trình build image. Ví dụ:
```DockerFile
RUN apt-get update
```
- **ENV**: Định nghĩa các biến môi trường
- **CMD**: Khác với **RUN** chỉ thị này cũng dùng để chạy một số câu lệnh, tuy nhiên nó sẽ được thực thi trong quá trình build container.
```DockerFile
CMD [service nginx start]
```
- **ENTRYPOINT**: Thực thi một số câu lệnh trong quá trình start container, những câu lệnh này sẽ được viết trong file .sh.
- **WORKDIR**: Thiết lập thư mục làm việc hiện tại cho các chỉ thị CMD, ENTRYPOINT, ADD thi hành.
- **VOLUME**: Chỉ thi tạo một ổ đĩa chia sẻ được giữa các container.
```dockerfile
VOLUME /docker_demo
```
- **EXPOSE**: Thông báo cho Docker rằng image sẽ lắng nghe trên các cổng được chỉ định khi chạy. Lưu ý là cái này chỉ để khai báo, chứ ko có chức năng nat port từ máy host vào container. Muốn nat port, thì phải sử dụng cờ -p (nat một vài port) hoặc -P (nat tất cả các port được khai báo trong EXPOSE) trong quá trình khởi tạo contrainer.
- **ADD** : Copy file, thư mục, remote file thêm chúng vào filesystem của image.
- **COPY** : Copy file, thư mục từ host machine vào image. Có thể sử dụng url cho tập tin cần copy.
## 3. Docker image 
- File nền của container. Từ các image này, bạn sẽ dùng nó để tạo ra các container. 
- Chúng ta có thể tự tạo image riêng cho mình hoặc pull từ DockerHub về.
- Một image có thể được tạo từ nhiều image khác.
## 4. Docker container
- Nó tương tự như một máy ảo, xuất hiện khi mình khởi chạy image. 
- Tốc độ khởi chạy container nhanh hơn tốc độ khởi chạy máy ảo rất nhiều và bạn có thể thoải mái chạy 4,5 container mà không sợ treo máy.
- Các files và settings được sử dụng trong container được lưu, sử dụng lại, gọi chung là images của docker. 
- Chúng ta có thể tạo nhiều container từ chỉ 1 image. 
- Container có thể started, running, restarted, and stopped.
## 5. Một số câu lệnh hay sử dụng

- List container đang chạy:

```none
 $ docker container ls
```

- List all container hiện có (kể cả đang chạy hay đã stop):

```none
$ docker ps –a
```

- Pull một image trên docker hub:

```none
$ docker pull <tên image>
```

- Start một container:

```none
$ docker start <tên container>
```

- Run một container chạy ngầm:

```none
$ docker run -d <tên image>
```

- Delete image/container:

```none
$ docker image/container rm <tên image/container >
```

- Stop a container cụ thể:

```none
$ docker stop <tên container>
```

- Stop all container:

```none
$ docker stop -a
```

- Show log a container:

```none
$ docker logs <tên container>
```

- Truy cập vào một container đang chạy:

```none
docker exec -it {container_name} bash
```