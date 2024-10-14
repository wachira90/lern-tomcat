# Lerning Tomcat

Guide to getting started with Apache Tomcat:

### 1. **Download and Install Tomcat**
   - Go to the [Tomcat download page](https://tomcat.apache.org/download-90.cgi) (choose the version you need, commonly Tomcat 9 or 10).
   - Select the version for your operating system (Windows, Linux, MacOS).
   - Download the **Core** package, usually the `.zip` (for Windows) or `.tar.gz` (for Linux/MacOS) version.

### 2. **Unpack the Archive**
   - **Windows**: Extract the `.zip` file into a directory (e.g., `C:\Tomcat`).
   - **Linux/MacOS**: Run the following command to extract the file:
     ```bash
     tar xvf apache-tomcat-9.x.x.tar.gz
     ```
     Then move the extracted folder to a suitable location (e.g., `/usr/local/tomcat`).

### 3. **Set Environment Variables**
   Set the `JAVA_HOME` environment variable to the location of your JDK.
   
   - **Windows**:
     - Right-click on **This PC** > **Properties** > **Advanced system settings**.
     - Go to **Environment Variables** and create a new variable:
       - Variable name: `JAVA_HOME`
       - Variable value: Path to your JDK (e.g., `C:\Program Files\Java\jdk-1.x.x`).
     - Add `%JAVA_HOME%\bin` to the **Path** variable.
   - **Linux/MacOS**:
     - Open the `.bashrc` or `.zshrc` file and add:
       ```bash
       export JAVA_HOME=/path/to/your/jdk
       export PATH=$JAVA_HOME/bin:$PATH
       ```
     - Reload the profile with `source ~/.bashrc` (or `~/.zshrc`).

### 4. **Start Tomcat**
   - **Windows**: Open a command prompt, navigate to the `bin` directory inside the Tomcat folder, and run:
     ```cmd
     startup.bat
     ```
   - **Linux/MacOS**: Open a terminal, navigate to the `bin` directory inside the Tomcat folder, and run:
     ```bash
     ./startup.sh
     ```
   Tomcat will start, and you can access the default homepage at: `http://localhost:8080`.

### 5. **Deploy a Web Application**
   Tomcat serves applications packaged as `.war` files. Here's how to deploy one:
   
   - Copy your `.war` file to the `webapps` directory of your Tomcat installation.
   - Tomcat will automatically deploy the application, and you can access it by visiting:
     ```
     http://localhost:8080/your-app-name
     ```

### 6. **Access Tomcat Manager (Optional)**
   The **Tomcat Manager** allows you to manage web apps from a browser. To enable it:
   - Open the `conf/tomcat-users.xml` file in the Tomcat directory.
   - Add the following lines to create a user with admin privileges:
     ```xml
     <role rolename="manager-gui"/>
     <role rolename="admin-gui"/>
     <user username="admin" password="password" roles="manager-gui,admin-gui"/>
     ```
   - Save the file and restart Tomcat.
   - Access the manager at: `http://localhost:8080/manager/html`.
   - Log in using the credentials defined in `tomcat-users.xml`.

### 7. **Stop Tomcat**
   - **Windows**: Run the following in the `bin` directory:
     ```cmd
     shutdown.bat
     ```
   - **Linux/MacOS**: Run:
     ```bash
     ./shutdown.sh
     ```

### 8. **Configure Tomcat (Optional)**
   You can configure ports, memory settings, and more by editing the following files:
   - **Server Port**: `conf/server.xml` (change `<Connector port="8080" />`).
   - **Memory Settings**: In `bin/setenv.sh` or `setenv.bat`, set `JAVA_OPTS` like:
     ```bash
     export JAVA_OPTS="-Xms512m -Xmx1024m"
     ```

---

Now you have Tomcat installed and can deploy and manage web applications! Let me know if you need more details on any of the steps.
