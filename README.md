# Version Control Experiment with Subversion (SVN) and Mercurial (Hg)

## **1. Subversion (SVN) Experiment**

### **Step 1: Create an SVN Repository**
```bash
mkdir -p ~/Desktop/DevOps/myrepo
svnadmin create ~/Desktop/DevOps/myrepo
```
![Screenshot from 2025-02-16 20-53-19](https://github.com/user-attachments/assets/0202096d-badd-41f9-ba92-86e947d068d0)


### **Step 2: Checkout the Repository**
```bash
cd ~/Desktop/DevOps
svn checkout file:///$(pwd)/myrepo myproject
```
**Output:**
```
Checked out revision 0.
```

### **Step 3: Add and Commit a File**
```bash
cd myproject
echo "Hello SVN" > file.txt
svn add file.txt
svn commit -m "Added file.txt"
```

### **Step 4: Check the Log and Update**
```bash
svn log
svn update
```
![Screenshot from 2025-02-16 21-09-51](https://github.com/user-attachments/assets/1951938c-734f-43bc-b266-a5578279c9ea)


## **2. Mercurial (Hg) Experiment**

### **Step 1: Initialize a Mercurial Repository**


```bash
mkdir -p ~/Desktop/DevOps/brepo
cd ~/Desktop/DevOps/brepo
hg init
```

![Screenshot from 2025-02-16 21-10-49](https://github.com/user-attachments/assets/3f848328-0edc-4742-be9b-9351adda3d39)


### **Step 2: Configure Username**
```bash
hg config --edit
```
Modify `[ui]` section to:
```ini
[ui]
username = asus <asus@example.com>
```


### **Step 3: Add and Commit a File**
```bash
echo "Hello Mercurial" > file.txt
hg add file.txt
hg commit -m "Added file.txt"
```

![Screenshot from 2025-02-16 21-18-07](https://github.com/user-attachments/assets/2f1cc21a-8cdf-44c5-8c48-c59fde6ca12a)


### **Step 4: Clone the Repository**
```bash
cd ~/Desktop/DevOps
hg clone brepo myclone
```

![Screenshot from 2025-02-16 21-21-41](https://github.com/user-attachments/assets/bfb25caf-73ff-4fc2-af66-68703e9bc455)


### **Step 5: Make Changes and Pull Updates**
```bash
cd brepo
echo "Another line" >> file.txt
hg commit -m "Updated file.txt with another line"
```

Now, pull updates in `myclone`:
```bash
cd ~/Desktop/DevOps/myclone
hg pull
hg update
```

![Screenshot from 2025-02-16 21-22-22](https://github.com/user-attachments/assets/5b4a3162-8264-45dd-8171-c77eb9fde16d)

![Screenshot from 2025-02-16 21-26-39](https://github.com/user-attachments/assets/65bae1d5-b2da-4d48-a52d-a855b7b7ffd6)


## **3. Hosting index.html with Readme.md on GitHub Pages**
1. **Create an `index.html` file** in your repository:
```
`<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SVN & Mercurial Report</title>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
            background-color: #f4f4f4;
        }
        #content {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body>
    <h2>SVN & Mercurial Practical Report</h2>
    <div id="content">Loading...</div>

    <script>
        fetch('README.md')
            .then(response => response.text())
            .then(text => {
                document.getElementById('content').innerHTML = marked.parse(text);
            })
            .catch(error => {
                document.getElementById('content').innerHTML = "<p>Error loading README.md</p>";
            });
    </script>
</body>
</html>
```

2. **Push Files to GitHub:**
```bash
git init
git add experiment.md index.html
git commit -m "Added experiment report and index.html"
git branch -M main
git remote add origin https://github.com/your-username/version-control-experiment.git
git push -u origin main
```

3. **Enable GitHub Pages:**
   - Go to **Repository Settings > Pages**.
   - Select **Branch: main** and save.

**Hosted Website Link**
 https://priyanshu443.github.io/Svn-Mercurial-/




