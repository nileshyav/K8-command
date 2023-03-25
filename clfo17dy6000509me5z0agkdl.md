---
title: "Jenkins Project: Upload file to s3"
datePublished: Sat Mar 25 2023 13:53:13 GMT+0000 (Coordinated Universal Time)
cuid: clfo17dy6000509me5z0agkdl
slug: jenkins-project-upload-file-to-s3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679750000954/0009d684-7e51-4675-9c37-6a3097b86f39.png
tags: aws, devops, jenkins, s3

---

In this project, we will upload a file to AWS s3 using Jenkins. For this project, you should have your AWS user access key ready for programmatic access.

So Now Let's start

Navigate to your Jenkins - x.x.x.x:8080 URL and Click "Manage Jenkins"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744486171/75149f22-0ee5-4c70-b097-2d94e5005043.jpeg align="center")

First You have to install a plugin - `Pipeline: AWS Steps`. for this Click on manage plugin then available plugin search and install it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744746824/3f5ba0ff-ae28-49a6-80dd-4f66cc9305b7.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744778907/c951bf14-ee20-4a30-9951-64a9b9549b06.jpeg align="center")

as you can see mine is already installed. after installing go to the dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744815947/761809c7-b088-440f-9579-abd1ae2a63d8.jpeg align="left")

Click "Manage Jenkins"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746816728/99dc9e20-e62d-44cf-8bed-39b8f79cadd6.jpeg align="left")

Click "manage credentials" here we will integrate aws with Jenkins.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746857913/b1cc2f19-4f9f-42e1-8767-53e51592fa84.jpeg align="left")

Click below down arrow for adding new credentials

Click "Add credentials"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744949701/cc586ca6-1918-48c3-9168-864e3fc1d004.jpeg align="left")

Select kind - AWS credentials option

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679744978280/bdb2ceed-421f-4707-aae8-9f00ee8195ff.jpeg align="left")

You can give any id name. but note it somewhere because it will be used in the pipeline code as below. give some cool description

```yaml
credentials: 'jenkins-test'
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679745004347/7f43a082-f3fa-4f6a-a646-a0ee72c4670f.jpeg align="left")

Enter your access key and secret key. then click on create button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679745197414/a1a561ab-fff6-4738-a954-12315871aec3.jpeg align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679745421765/b90b8830-962c-46b4-99f7-592bc5078aff.jpeg align="left")

Go to "Dashboard". Now we have to create a new bucket in AWS account so that we can upload a new file. go to S3

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751147960/ef39948b-7a4d-4675-aa93-72a9caef0244.jpeg align="left")

Click "Create bucket"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751301733/2bb7f0fb-56a7-49a2-ad15-8fca2cf4c1ad.jpeg align="left")

choose your region and give a unique name to your bucket. copy somewhere bucket name, we will use it later.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751391662/92a13e17-a85f-44d9-8ff2-38cc17f1bea0.jpeg align="left")

keep all default option

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751477935/87029786-a3fa-4fa2-ada7-3a87b2757fbe.jpeg align="left")

Click "Create bucket"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751657358/5efacacd-4879-4c4e-a7a5-b4594e3954d2.jpeg align="left")

My bucket name is testing-jenkins123

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751728504/878accb1-5f4a-498f-abf9-0704c4110647.jpeg align="left")

Now we will create a pipeline Click "New Item"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679745958931/c4b42662-9eea-4a9f-874b-1a5d060ace75.jpeg align="left")

Give a name, select pipeline then click ok

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746001063/cd4d00ac-edd5-4bf1-84cc-2902976af0f0.jpeg align="left")

Scroll down to pipeline section.

![Screenshot of: Scroll down to pipeline section. and paste it](https://colony-recorder.s3-accelerate.amazonaws.com/files/2023-03-24/833717c2-55c1-40c4-a18c-0640e73a0e8c/ascreenshot.jpeg?AWSAccessKeyId=AKIA2JDELI43YPETRQSC&Signature=C0aESupgb9DSx%2FYkja59JH7044Y%3D&Expires=1679762649 align="left")

**Paste below pipeline code but change some information - like credentials, region and bucket name. then click Save**

```bash
pipeline{
    agent any

    stages{
        stage("Aws test credentials"){
            steps{
                withAWS(credentials: 'your-id-name', region: 'your-region'){
                    sh 'echo "Hello DevOps" > hello.txt'
                    s3Upload (acl: 'Private' , bucket: 'your-bucket-name' , file: 'hello.txt')
                    s3Download(file:'downloaded.txt', bucket:'your-bucket-name', path:'hello.txt',force:true) 
                    sh "cat downloaded.txt"
                   
                }
            }
        }
    }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746165922/12f176b5-ef18-4b42-bdf6-50287b153293.jpeg align="left")

Click "Build Now"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746288005/48958ac4-9d66-475a-9aa6-dd921515696b.jpeg align="left")

**as you can see your pipeline successfully runs. now let's check the console log.**

Click "Console Output"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679746357167/162cd467-5f35-407f-8bc0-4ef2a2fe9c5a.jpeg align="left")

our pipeline finished successfully and we got a message Hello India.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679748527194/dae96578-9dba-454a-93eb-ca85ed0fc3ff.jpeg align="left")

Now we will test whether that file is created in a bucket or not.

go inside your bucket and boom hello.txt is created in our bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679751981860/b0c677e0-8860-4406-a012-122ebc79bbea.jpeg align="left")

Congratulation you have successfully finished a Jenkins project. I will see you in the next project. Bye