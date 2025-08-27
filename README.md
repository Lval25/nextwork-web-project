# NextWork Web Project 🚀  

A **simple Java web application** deployed on an **AWS EC2 instance**, with version control using **GitHub**.  

## **Project Overview**
This project demonstrates the setup and deployment of a lightweight Java web application on an Amazon Linux EC2 instance. It covers key steps from instance setup, environment configuration, and Maven project creation to GitHub integration and version control.

---

## **Steps & Setup**

### **1️⃣ Launch EC2 and SSH Access**
- Created an **EC2 instance**  
- Generated and used a **key-pair** for secure SSH login:
```bash
ssh -i nextwork-keypair.pem ec2-user@<ec2-public-ip>
```

---

### **2️⃣ Install Maven**
```bash
wget https://archive.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz
sudo tar -xzf apache-maven-3.5.2-bin.tar.gz -C /opt
echo "export PATH=/opt/apache-maven-3.5.2/bin:$PATH" >> ~/.bashrc
source ~/.bashrc
```

---

### **3️⃣ Install Amazon Corretto (Java 8)**
```bash
sudo dnf install -y java-1.8.0-amazon-corretto-devel
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64
export PATH=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64/jre/bin/:$PATH
```

---

### **4️⃣ Generate Maven Web App**
```bash
mvn archetype:generate    -DgroupId=com.nextwork.app    -DartifactId=nextwork-web-project    -DarchetypeArtifactId=maven-archetype-webapp    -DinteractiveMode=false
```

---

### **5️⃣ Customize the App**
Edited the `index.jsp` file to include:
```html
<html>
<body>
<h2>Hello Perry</h2>
<p>This is my NextWork web application working!</p>
</body>
</html>
```

Later updated to:
```html
<p>If you see this line in Github, that means your latest changes are getting pushed to your cloud repo :o</p>
```

---

### **6️⃣ Install Git on EC2**
```bash
sudo dnf update -y
sudo dnf install git -y
```

---

### **7️⃣ Initialize Git & Push to GitHub**
- Created a new GitHub repository: **`nextwork-web-project`**
- Initialized Git inside the EC2 environment
```bash
git init
git remote add origin git@github.com:Lval25/nextwork-web-project.git
git add .
git commit -m "Updated index.jsp with new content"
git push -u origin master
```
- Configured a **GitHub token** for secure pushes  
- Made another update and pushed changes:
```bash
git commit -m "Add new line to index.jsp"
git push
```

---

## **Key Takeaways**
- Learned how to **deploy a Maven-based Java web app** on AWS EC2.  
- Practiced **remote login, environment setup, and Git version control**.  
- Established a simple **DevOps pipeline foundation** with GitHub for version management.  

