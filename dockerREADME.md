# DockerClassroom
First Alpine Linux Containers
1.0 Running your first container
docker container run hello-world

![image](https://github.com/user-attachments/assets/5d8e022a-d033-44f0-afe6-8e66939f7ee9)

1.1 Docker Images

docker image pull alpine

![image](https://github.com/user-attachments/assets/ab5ca033-6dfa-4fd6-a5c0-7d7bb4d5286e)
docker image ls

![image](https://github.com/user-attachments/assets/e2ecb5cb-3c58-44d4-be2f-a842d8eebdb4)

1.1 Docker Container Run

docker container run alpine ls -l

![image](https://github.com/user-attachments/assets/a43798ec-85d2-4255-b257-84da894c8f2e)

docker container run alpine echo "hello from alpine"

![image](https://github.com/user-attachments/assets/50026a8d-b5e6-4a7d-9e8d-de0a271f18fc)
docker container run alpine /bin/sh

![image](https://github.com/user-attachments/assets/28db9cb3-edf5-4567-aba9-5d5db2d3b002)

docker container run -it alpine /bin/sh
 
![image](https://github.com/user-attachments/assets/f2423820-9c45-4f96-88e6-745412978653)

docker container ls

![image](https://github.com/user-attachments/assets/89883ca1-9fc0-4e7f-8bae-1d90f6d32806)

docker container ls -a

![image](https://github.com/user-attachments/assets/f0b1bdcb-d514-4c26-b55d-123faa06001a)

1.2 Container Isolation

docker container run -it alpine /bin/ash

 echo "hello world" > hello.txt

 ls

![image](https://github.com/user-attachments/assets/d6e7f970-ef3a-4cc9-9348-f9ceba2a47e5)

docker container run alpine ls

![image](https://github.com/user-attachments/assets/df329bc1-a65a-4e3c-b2d4-40ba4a5d94b0)


docker container ls -a

![image](https://github.com/user-attachments/assets/3327d395-dd30-4bcc-b09a-2256afe0920e)

docker container start <container ID>

![image](https://github.com/user-attachments/assets/3096af29-0b5a-4d27-b977-08cd185b128a)

docker container ls

![image](https://github.com/user-attachments/assets/d07dceaa-b1ff-4304-b12d-f811634e697b)

docker container exec <container ID> ls

![image](https://github.com/user-attachments/assets/a4542a4b-67b0-46d9-9b4e-407ccd21ca3a)













