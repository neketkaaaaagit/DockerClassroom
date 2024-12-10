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



Doing More With Docker Images
Image creation from a container

docker container run -it ubuntu bash

![image](https://github.com/user-attachments/assets/ce91da00-379c-4dac-a222-8a2950aa4b99)

apt-get update

![image](https://github.com/user-attachments/assets/0aec3b4f-73f3-45f5-a559-c78abe83dc84)

apt-get install -y figlet

![image](https://github.com/user-attachments/assets/56a103a9-3064-47d3-a813-73126327db54)

figlet "hello docker"

![image](https://github.com/user-attachments/assets/6130f3f3-9843-4901-9b2d-f1e21d9da588)

exit

![image](https://github.com/user-attachments/assets/9ffaba8c-faf5-46a5-8abf-83de3ecd9ae4)

docker container diff <container ID>

![image](https://github.com/user-attachments/assets/8c23979d-01e6-48a3-96ba-8ae6e23ac8ce)

docker container commit CONTAINER_ID

![image](https://github.com/user-attachments/assets/848bd217-6121-4f68-8bf8-b7473c4f4c0b)

docker image ls

![image](https://github.com/user-attachments/assets/759a988f-2457-49ae-97e0-5c521bf13828)

docker image tag <IMAGE_ID> ourfiglet

![image](https://github.com/user-attachments/assets/a98281e0-4c4f-4d7d-9366-4a887eb050e0)

docker image ls

![image](https://github.com/user-attachments/assets/800bf035-3fd8-42c1-879d-e9017eab8591)

docker container run ourfiglet figlet hello

![image](https://github.com/user-attachments/assets/3d50cda2-f007-4536-a201-043e87320ed2)

Image creation using a Dockerfile

![image](https://github.com/user-attachments/assets/26733f89-13f9-478e-8bfa-8e804c653573)

FROM alpine
RUN apk update && apk add nodejs
COPY . /app
WORKDIR /app
CMD ["node","index.js"]

docker image build -t hello:v0.1 .

![image](https://github.com/user-attachments/assets/21f5fc58-a234-4796-8901-e3995bf049df)

docker container run hello:v0.1

![image](https://github.com/user-attachments/assets/7032afb1-ce1e-4958-a0d5-1b5c156ceac0)

Image layers

docker image ls

![image](https://github.com/user-attachments/assets/0628a12c-0a0f-40ac-a8cb-41c2888f9be8)

docker image history <image ID>

![image](https://github.com/user-attachments/assets/1fe61f8b-8f90-44f8-9281-4b6537edbb8e)

echo "console.log(\"this is v0.2\");" >> index.js

![image](https://github.com/user-attachments/assets/8dba8ce4-86d2-4860-bddd-8e5502bb4984)

docker image build -t hello:v0.2 .

![image](https://github.com/user-attachments/assets/8965b8e3-3b35-4eb8-b908-28c79f509237)

docker image pull alpine

![image](https://github.com/user-attachments/assets/99411860-f27b-4baa-a32e-9929a6c53eef)

docker image inspect alpine

![image](https://github.com/user-attachments/assets/32d1316e-2bd4-46c9-a3a7-96638138a033)

docker image inspect --format "{{ json .RootFS.Layers }}" alpine

![image](https://github.com/user-attachments/assets/19af7dd0-e3e2-436f-9773-3148a89bf763)

docker image inspect --format "{{ json .RootFS.Layers }}" <image ID>

![image](https://github.com/user-attachments/assets/5f042053-7f47-4d69-a2b0-12d7ad9f0b9f)

Swarm Mode Introduction for IT Pros
































