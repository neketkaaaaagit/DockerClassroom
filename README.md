![image](https://github.com/user-attachments/assets/33d55dfc-933a-432e-8b89-a1761ba38bf3)![image](https://github.com/user-attachments/assets/b1dd7593-8f1a-41cd-831f-b777477b1ea6)# DockerClassroom
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

Initialize Your Swarm

docker swarm init --advertise-addr $(hostname -i)

![image](https://github.com/user-attachments/assets/147784f6-ab5a-4b51-a1dc-9baaae5351d0)

docker node ls

![image](https://github.com/user-attachments/assets/3e43c780-a226-4e3f-ae54-9b84a665ed55)

git clone https://github.com/docker/example-voting-app

![image](https://github.com/user-attachments/assets/bccadf47-a615-4ca7-8c77-af0f728e2741)

cd example-voting-app

![image](https://github.com/user-attachments/assets/07d94d49-16bd-49f4-ae5d-b5026a075b2a)

cat docker-stack.yml

![image](https://github.com/user-attachments/assets/fefe12a6-73ed-4cd4-8d43-85a724c95fa6)

docker stack deploy --compose-file=docker-stack.yml voting_stack

![image](https://github.com/user-attachments/assets/8a8581c5-9cad-4184-9b16-06e12c548e83)

docker stack ls

![image](https://github.com/user-attachments/assets/c229e71c-bc35-4c60-a013-588b5326a68a)

docker stack services voting_stack

![image](https://github.com/user-attachments/assets/7fb7c6d7-4c1f-4906-bf29-e06d2d0ee9fd)

docker service ps voting_stack_vote

![image](https://github.com/user-attachments/assets/53b3a03d-2213-4acd-9179-22fd9cb99cdc)

Scaling An Application

docker service scale voting_stack_vote=5

![image](https://github.com/user-attachments/assets/4903f5f8-07dd-4e47-bd1f-f74de9ebbe3a)

docker stack services voting_stack

![image](https://github.com/user-attachments/assets/a5771f6e-8758-41b4-94fb-6bb1eb542a7f)

Docker Enterprise Edition

![image](https://github.com/user-attachments/assets/15a7f26e-d5f2-4003-a6bf-4a8c80ef9793)

Security
Seccomp profiles

Step 1: Clone the labs GitHub repo

git clone https://github.com/docker/labs

![image](https://github.com/user-attachments/assets/dd881530-cb67-49fd-acd8-eecb3e41aafa)

cd labs/security/seccomp

![image](https://github.com/user-attachments/assets/081891d1-3448-4d8f-9afa-4de7774ad337)

Step 2: Test a seccomp profile

docker run --rm -it --cap-add ALL --security-opt apparmor=unconfined --security-opt seccomp=seccomp-profiles/deny.json alpine sh

![image](https://github.com/user-attachments/assets/f4ba6abb-bf53-4477-a1a1-14c3b0434784)

cat seccomp-profiles/deny.json

![image](https://github.com/user-attachments/assets/df205de0-83c7-45db-8cd1-087be1b46c6f)

Step 3: Run a container with no seccomp profile

docker run --rm -it --security-opt seccomp=unconfined debian:jessie sh

![image](https://github.com/user-attachments/assets/cb17acc5-b129-490f-be3d-f0d217176fa9)

whoami

![image](https://github.com/user-attachments/assets/40e4872c-d546-4f3b-9940-c64d7d405db5)

 unshare --map-root-user --user
 
 whoami

![image](https://github.com/user-attachments/assets/d2594244-a306-4013-9309-ee5a75603f44)

apk add --update strace

![image](https://github.com/user-attachments/assets/6bc15936-0cfa-40cc-bdd9-acc17b8bfc50)

strace -c -f -S name whoami 2>&1 1>/dev/null | tail -n +3 | head -n -2 | awk '{print $(NF)}'

![image](https://github.com/user-attachments/assets/aad2e849-ac4d-4177-a54b-994c62d64fc3)

strace whoami

![image](https://github.com/user-attachments/assets/0949c005-37ec-469b-b328-309bd849205c)

Step 4: Selectively remove syscalls

docker run --rm -it --security-opt seccomp=./seccomp-profiles/default-no-chmod.json alpine sh

![image](https://github.com/user-attachments/assets/5b7745de-65ec-40e4-923a-22a91c07dd3e)

chmod 777 / -v

![image](https://github.com/user-attachments/assets/eabb9485-75f7-4017-b71d-18544c1116f7)

exit

![image](https://github.com/user-attachments/assets/b5d326b4-a84c-43f1-8782-c527cf2828d7)

docker run --rm -it --security-opt seccomp=./seccomp-profiles/default.json alpine sh

![image](https://github.com/user-attachments/assets/eee894ce-c2b6-4bf5-9244-42c0bad2230e)

chmod 777 / -v

![image](https://github.com/user-attachments/assets/1fb9d349-e022-4b35-baef-f60b992957d1)

exit

cat ./seccomp-profiles/default.json | grep chmod

![image](https://github.com/user-attachments/assets/16e7f5ad-89e2-4b51-aefe-0e9e0e41ff13)

cat ./seccomp-profiles/default-no-chmod.json | grep chmod

![image](https://github.com/user-attachments/assets/ff439d82-94b7-4121-bff1-b7ba7dbbf6a9)

Step 5: Write a seccomp profile

![image](https://github.com/user-attachments/assets/714e363b-266c-4efd-ac87-36f1ac74fd18)

Security Lab: Capabilities

Step 1: Introduction to capabilities

Step 2: Working with Docker and capabilities

![image](https://github.com/user-attachments/assets/c6e5645c-2aaf-4d90-98de-d8fd2370bf33)

![image](https://github.com/user-attachments/assets/694549e3-715f-4aad-b79f-a34625757b78)

 docker run --rm -it alpine chown nobody /

 ![image](https://github.com/user-attachments/assets/e9284990-09f8-4ec7-a07d-8749701afd3c)

 docker run --rm -it --cap-drop ALL --cap-add CHOWN alpine chown nobody /

 ![image](https://github.com/user-attachments/assets/efaf4d89-beac-41ea-8599-67e4b7042037)

docker run --rm -it --cap-drop CHOWN alpine chown nobody /

 ![image](https://github.com/user-attachments/assets/d6e8a2fb-d289-448b-9242-8c22d8c9193a)

 docker run --rm -it --cap-add chown -u nobody alpine chown nobody /

 ![image](https://github.com/user-attachments/assets/738f4ebb-d673-4bb4-88a6-bdf9aa5e4678)

 Step 4: Extra for experts

 docker run --rm -it alpine sh -c 'apk add -U libcap; capsh --print'

 ![image](https://github.com/user-attachments/assets/bbdd8984-9c23-4254-8a5d-fd93cb742712)

 Experimenting with capabilities

 docker run --rm -it alpine sh -c 'apk add -U libcap;capsh --help'

 ![image](https://github.com/user-attachments/assets/af92ef85-8e31-48f6-8fdc-20241eabd505)

Networking

Section #1 - Networking Basics

Step 1: The Docker Network Command

docker network

![image](https://github.com/user-attachments/assets/f3b66de1-f060-440e-ac66-87a55bf9c9fd)

Step 2: List networks

docker network ls

![image](https://github.com/user-attachments/assets/4852dbe8-5c57-459c-9b1e-7287a569240a)

Step 3: Inspect a network

docker network inspect bridge

![image](https://github.com/user-attachments/assets/d4244870-9f1d-41af-a99a-b9bc22557f8c)

Step 4: List network driver plugins

docker info

![image](https://github.com/user-attachments/assets/937fb94e-5af2-4d97-84bf-928d44678809)

Section #2 - Bridge Networking

Step 1: The Basics

docker network ls

![image](https://github.com/user-attachments/assets/7c053ae9-3276-4d11-b8a0-f0c65ef94ac8)

apk update

apk add bridge

![image](https://github.com/user-attachments/assets/b01d3973-ce68-48ee-a3f8-100229b38bfe)

brctl show

![image](https://github.com/user-attachments/assets/eec38c22-16da-4028-9920-c737af9db416)

ip a

![image](https://github.com/user-attachments/assets/958c7cee-5cc3-46a2-b815-20731442a9a9)

Step 2: Connect a container

docker run -dt ubuntu sleep infinity

![image](https://github.com/user-attachments/assets/2f00749c-e940-4181-82ba-e885bcda6975)

docker ps

![image](https://github.com/user-attachments/assets/0bc4adb7-8533-4ed9-be62-df54bc0e2018)

brctl show

![image](https://github.com/user-attachments/assets/a18c3df5-fb54-462f-8322-6c90be16ba7c)

docker network inspect bridge

![image](https://github.com/user-attachments/assets/ec88405c-90c3-4bb1-a763-107d6a3394ca)

Step 3: Test network connectivity

docker exec -it yourcontainerid /bin/bash

![image](https://github.com/user-attachments/assets/649828f8-7082-4817-9596-a542149fa210)

apt-get update && apt-get install -y iputils-ping

![image](https://github.com/user-attachments/assets/dd31525a-de54-44df-9100-192e11fc34f3)

ping -c5 www.github.com

![image](https://github.com/user-attachments/assets/0d21c976-ba28-4b81-a8b3-2d8bb049af34)

docker stop yourcontainerid

![image](https://github.com/user-attachments/assets/bd485305-1e6b-41d5-9c1a-5d056bd483cc)

Step 4: Configure NAT for external connectivity

docker run --name web1 -d -p 8080:80 nginx

![image](https://github.com/user-attachments/assets/d8416c87-3cf4-445e-ac63-893c665f2a96)

docker ps

![image](https://github.com/user-attachments/assets/f7a442aa-738e-4d21-a5e0-7685365bb389)

curl 127.0.0.8080

![image](https://github.com/user-attachments/assets/cb19fe2f-3e0d-4393-b9ba-a3d252be75d8)

Section #3 - Overlay Networking

Step 1: The Basics

docker swarm init --advertise-addr $(hostname -i)

![image](https://github.com/user-attachments/assets/9aa981f3-2b5e-497f-a4b6-01dee2d0c50b)

docker node ls

![image](https://github.com/user-attachments/assets/99412534-7699-4f67-82ae-a112344a7d20)

Step 2: Create an overlay network

docker network create -d overlay overnet

![image](https://github.com/user-attachments/assets/27d7f329-1400-492e-9d70-a6030fe207d6)

docker network ls

![image](https://github.com/user-attachments/assets/d4379efe-1867-4cf7-bcf2-ce84b086e576)

docker network ls first terminal

![image](https://github.com/user-attachments/assets/ce9eea1a-9aa9-4fb2-8193-322794eee9bc)

docker network inspect overnet

![image](https://github.com/user-attachments/assets/2a7c3237-542c-4d55-86f4-ab5fcad26172)

Step 3: Create a service

docker service create --name myservice \
--network overnet \
--replicas 2 \
ubuntu sleep infinity

![image](https://github.com/user-attachments/assets/21efea73-b20e-44c2-a6d1-4d8dcbb0ae46)

docker service ls

![image](https://github.com/user-attachments/assets/8ff5237a-96a9-437f-b816-cb5147651d52)

docker service ps myservice

![image](https://github.com/user-attachments/assets/778babec-93e8-4313-aa56-cd5e3dd75f97)

docker network ls

![image](https://github.com/user-attachments/assets/c1f4eada-ac9b-47ca-b855-ef9717e869a8)

docker network inspect overnet

![image](https://github.com/user-attachments/assets/da622afe-6502-4313-b4f3-1ed8fa0849fb)

![image](https://github.com/user-attachments/assets/8f44097b-b1ac-4623-900d-d2779c571f4d)

Step 4: Test the network

docker network inspect overnet

![image](https://github.com/user-attachments/assets/aff6d2b1-2f43-43db-aa83-6a9c2d2f905a)

docker ps (node 2)

![image](https://github.com/user-attachments/assets/45a578cd-c932-4127-b50f-ff081e79610b)

docker exec -it yourcontainerid /bin/bash

![image](https://github.com/user-attachments/assets/24fcac85-6ab9-45da-b1e8-43d9689e35d3)

apt-get update && apt-get install -y iputils-ping

![image](https://github.com/user-attachments/assets/b064f93b-9efc-4af9-96d2-0e8605d502fe)

ping -c5 10.0.1.3

![image](https://github.com/user-attachments/assets/bbf3a6c1-de5b-4ea1-84b0-1e06fafd200e)

Step 5: Test service discovery

cat /etc/resolv.conf

![image](https://github.com/user-attachments/assets/7f382d06-70ae-44fb-9094-ba49c501f7a4)

docker service inspect myservice

![image](https://github.com/user-attachments/assets/cab00df9-8ccb-4e78-b0a9-17d7ff794140)

Cleaning Up

docker service rm myservice

![image](https://github.com/user-attachments/assets/d9da56f5-6cb9-4537-bb48-28378731bbc2)

docker kill containerid

![image](https://github.com/user-attachments/assets/7fb134e7-cacc-48e3-be3c-d871a7c20b08)

docker swarm leave --force

![image](https://github.com/user-attachments/assets/cec3ce02-4617-4afb-9583-9cfbb1df8bab)

Docker Orchestration Hands-on Lab

Section 2: Configure Swarm Mode

docker run -dt ubuntu sleep infinity

![image](https://github.com/user-attachments/assets/164648cc-ff78-431d-a6c1-d47f431d6f53)

docker ps

![image](https://github.com/user-attachments/assets/b7f75ca0-ad8a-4073-830d-2ee518a66d4a)

Step 2.1 - Create a Manager node

![image](https://github.com/user-attachments/assets/785308a9-8a1d-4924-b56a-9907f22d0338)

docker info

![image](https://github.com/user-attachments/assets/f76d36f5-a240-44a3-8e54-cade12065068)

docker swarm join --token SWMTKN-1-69xqv570xuqhn7trxnjb4yzl2l8arsrvk1e7zk6tvwc8im4ive-6hx702rnq9cfi4queec69lfy8 192.168.0.8:2377

![image](https://github.com/user-attachments/assets/cece26c7-fe87-4a10-bc0e-9983461c4ba4)

docker node ls

![image](https://github.com/user-attachments/assets/e1d1f044-66be-4ebe-bad3-f05c5bb50b69)

Section 3: Deploy applications across multiple hosts

Step 3.1 - Deploy the application components as Docker services

docker service create --name sleep-app ubuntu sleep infinity

![image](https://github.com/user-attachments/assets/c0517f31-e2c5-49e9-a503-d897c091656a)

iltwywlji6c3qp4el6d49phz3

docker service ls

![image](https://github.com/user-attachments/assets/cbb828a8-e4bd-4882-a423-6da4b1c2a36a)

Section 4: Scale the application

docker service update --replicas 7 sleep-app

![image](https://github.com/user-attachments/assets/2cc02983-cc94-4bc8-a95f-db6783759c77)

docker service ps sleep-app

![image](https://github.com/user-attachments/assets/02af4e2a-254a-49ef-99ce-ca96be92ffa9)

docker service update --replicas 4 sleep-app

![image](https://github.com/user-attachments/assets/64fbcc88-66f8-4607-a443-d324e4365b47)

docker service ps sleep-app

![image](https://github.com/user-attachments/assets/c429f667-ef59-47f7-a58d-d52d0e288e0b)

Section 5: Drain a node and reschedule the containers

docker node ls

![image](https://github.com/user-attachments/assets/60e7c403-e345-4700-b304-2d7b88115f64)

docker ps (node 2)

![image](https://github.com/user-attachments/assets/467a5267-6ffd-4e36-9045-2c2230a72cd9)


docker node ls

![image](https://github.com/user-attachments/assets/c9daa6f3-07ef-4635-bbc2-afddb6259b42)

docker node update --availability drain yournodeid

![image](https://github.com/user-attachments/assets/c512cd5e-5bca-4f40-b633-5ee3737ed44c)

docker node ls (node - drain)

![image](https://github.com/user-attachments/assets/bdd5684e-6a7a-4998-b310-a132ba60649e)

docker ps (node 2)

![image](https://github.com/user-attachments/assets/e349b17e-11f9-47dd-8afb-c41dc3f4ea86)

docker service ps sleep-app

![image](https://github.com/user-attachments/assets/f367f12e-eb47-433e-8593-6a88fe51ef7a)

Cleaning Up

docker kill yourcontainerid

![image](https://github.com/user-attachments/assets/28b00bb1-5484-42b2-aa9f-32f151a92db1)

docker swarm leave --force

![image](https://github.com/user-attachments/assets/ff1d607b-b59d-45e8-974b-aa47a25700ac)

Docker for IT Pros and System Administrators Stage 3

Docker EE DDC Implementation Considerations

![image](https://github.com/user-attachments/assets/bd9c59a6-3454-413a-917d-730e8f1b4a23)

Service Discovery and Load Balancing with Docker Universal Control Plane

![image](https://github.com/user-attachments/assets/3ce718b9-aaf9-44ee-836f-53ff57918135)

An Introduction to Storage Solutions for Docker CaaS

Docker Reference Architecture: Designing Scalable, Portable Docker Container Networks

Docker Reference Architecture: Securing Docker EE and Security Best Practices

Docker Reference Architecture: Docker EE Best Practices and Design Considerations

Docker Reference Architecture: Development Pipeline Best Practices Using Docker EE

![image](https://github.com/user-attachments/assets/143ed9f5-0325-4970-ad9f-7c462845fa09)

Download Docker

![image](https://github.com/user-attachments/assets/a875b278-08a2-44d5-a29d-6266b7191d4c)

Stage 3: Moving to Production

Sign up for the Docker Community

https://hub.docker.com/u/neketkaaaaa

![image](https://github.com/user-attachments/assets/85d3a0b2-8b68-4c20-873f-815ee6e1c45b)

Explore the Docker documentation

![image](https://github.com/user-attachments/assets/fa353265-7c59-41f3-8af3-f251bd27c243)



Getting Started Walk-through for Developers
Stage 1: The Basics

Self-guided in-browser tutorials
Docker for Beginners - Linux

git clone https://github.com/dockersamples/linux_tweet_app

![image](https://github.com/user-attachments/assets/e8d9242e-d393-4827-8982-370d4703233e)

docker container run alpine hostname

![image](https://github.com/user-attachments/assets/d7a0f6bc-d13f-4a8a-8923-094aa7f11f42)

docker container ls --all

![image](https://github.com/user-attachments/assets/79dd178f-cd0f-430f-908d-1ce354df8158)

 docker container run --interactive --tty --rm ubuntu bash

![image](https://github.com/user-attachments/assets/90ceca27-1309-4935-aaed-9af70c56771a)

ls / 

![image](https://github.com/user-attachments/assets/d314ad4b-5e9b-4fa0-a5f0-aeba0c198fec)

ps aux

![image](https://github.com/user-attachments/assets/028af03e-749f-4754-b2ff-daa5bf006c0b)

cat /etc/issue

![image](https://github.com/user-attachments/assets/9e022d74-ac3d-4b75-be4c-77ff59eacffb)

exit 

cat /etc/issue

![image](https://github.com/user-attachments/assets/3952e4a8-75bb-4a1e-8522-992795818eb8)

MYSQL Container

 docker container run \
 --detach \
 --name mydb \
 -e MYSQL_ROOT_PASSWORD=my-secret-pw \
 mysql:latest

 ![image](https://github.com/user-attachments/assets/defd0eb4-ad00-4ac8-b7ed-9583f37863e3)

 docker container ls

 ![image](https://github.com/user-attachments/assets/3e910b2a-4daa-459b-9097-b236b412d737)

 docker container logs mydb

 ![image](https://github.com/user-attachments/assets/62679c87-3142-4084-95ea-2605010b123b)

 docker container top mydb
 
 ![image](https://github.com/user-attachments/assets/bb3c23be-6db1-4e68-97c1-9759a4f3121f)

docker exec -it mydb \
mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version

 ![image](https://github.com/user-attachments/assets/17915a1d-8eca-4253-9e28-dc0ab672161c)

 docker exec -it mydb sh

 ![image](https://github.com/user-attachments/assets/94535224-1e46-4285-872e-6a2895260a69)

 mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version

 exit

![image](https://github.com/user-attachments/assets/c29491c1-0af8-4ebd-8e44-0df35cbb9d1b)

Task 2: Package and run a custom app using Docker

cd ~/linux_tweet_app

cat Dockerfile

![image](https://github.com/user-attachments/assets/e2218cf2-4ab5-4055-9900-a08e15c242af)

export DOCKERID=neketkaaaaa

echo $DOCKERID

docker image build --tag $DOCKERID/linux_tweet_app:1.0 .

![image](https://github.com/user-attachments/assets/a3994c78-b43a-49ca-bd2e-c68e983b6e2a)

docker container run \
 --detach \
 --publish 80:80 \
 --name linux_tweet_app \
 $DOCKERID/linux_tweet_app:1.0

 ![image](https://github.com/user-attachments/assets/a9905cbb-05ca-4859-a1d6-9b218f589262)

 ![image](https://github.com/user-attachments/assets/48ac3260-a195-43db-b0be-512bfb8d6b2c)

 docker container rm --force linux_tweet_app

 ![image](https://github.com/user-attachments/assets/a20bb079-2f5a-44bb-9954-658d929bdf5a)

 удалился






























































































































































