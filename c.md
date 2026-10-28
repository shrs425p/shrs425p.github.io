# Agile SD and DevOps Lab – TE CSE (AIML) – Steps, Commands & Code

> Only step numbers, steps, commands, code and expected results. No theory.
> The slides contain two experiments titled "Exp7" (Docker Compose and Monitoring). Both are included below. Slide numbering for Exp9 skips Step 8; original numbers are kept.

---

# Exp1 – Agile Software Project Lifecycle using Jira

**Step 1:** Sign up for a free Jira account → Name your first project → keep all default selections.
*Expected:* Jira workspace for the created project opens (free plan, 10 users).

**Step 2–5:** Theory only (skipped).

**Step 6:** Create 2nd project.
- Click Jira logo → home page
- Projects → `+` → select **Kanban** → **Use template** (default)
- Select **Team-managed**
- Project details → Name: `Learning Jira Project Creation`
- **Create project** → Invite teammates → **Skip**

*Expected:* Kanban board with 3 columns: **To do / In progress / Done**.

**Step 7:** Create tasks on the board.
1. Go to **To do** → Create task: `Discuss the project with customer` → click **Create work item**
2. Create another task: `Discuss with developers` → **Create work item**
3. Drag tasks across: To do → In progress → Done

*Expected:* Tasks move between the 3 columns.

**Step 8:** Create task with dates.
- Board → **Create** → select status
- Summary: `Start development on project model`
- Assignee: *your name*
- Due date: `30.8.26`
- Start date: `1.8.26`
- **Create**

*Expected:* Task appears on the Board.

**Step 9:** Backlog.
- Project: Learning Jira → 3 dots → **Project Settings** → **Features** → enable **Backlog**
- Open **Backlog** (appears before Board) → create `User Acceptance Testing`
- Change status to To do / In progress, or drag it to To do

*Expected:* Backlog tab visible; task moves to board when status changed.

**Step 10:** Child task / subtask.
- Create task in To do: `Develop Module 2 software`
- Open task → click `+` → **Create child work item**: `Develop login submodule` → Create
- Click `+` again → `Change homepage picture` → Create

*Expected:* Main task cannot go from In progress → Done until all child tasks are Done.

### Epic / Story / Task / Subtask example (Project: Software Development)

| Concept | Example |
|---|---|
| Epic | Password Reset feature |
| Story | As a user, I want to reset my password so that I can regain access. |
| Task | Design UI, Build API, Setup Email Notification |
| Subtask | Create wireframe, Validate input, Generate token, Create template |

**Step 11:** Create 3rd project.
- Jira → Projects → `+` → **Kanban** → **Use template** → **Team-managed**
- Name: `Software Development` → Create project → Invite teammates → Skip

**Step 12:** Configure work types.
- Project Software Development → 3 dots → **Project Settings**
  1. **Features** → enable **Backlog**
  2. **Work types** (expand) → **Add work type** → `Bug` → Add
  3. Same for `Story` → Add

*Expected:* Work types listed: Epic, Bug, Story, Task.

**Step 13:** Create Epic and Story.
- Board is blank → go to **Backlog**
- Select **Epic** → enable **Show epic panel** → **Create epic**: `Password reset feature`
- Go to Board → **To do** → Create task → select **Story** type: `As a registered user, I want to get option to reset my password to regain access.`

**Step 14:** Link story to epic and rename.
- Backlog → in the story click **+Epic** → select the created epic
- Go to Epic → **View all details** → rename to `Epic1: Password Reset`
- Rename story to `Story1: <text>`

*Expected:* Story visible on board with epic color tag (pink).

**Step 15:** Create tasks under story (To do).
1. `Password Reset User Interface Design`
2. `Password Reset functionality using API`
3. `Email Configuration`

*Expected:* Story moves to Done only when all 3 tasks are Done.

**Step 16:** Create subtasks.
- Open task `Password reset UI Design` → `+` → **Create child work item**
  1. `Discuss with Solution Architect and UI Designer` → Create
  2. `+` → `Assign Developer`
  3. `+` → `Start Development`

*Expected:* Main task can move to Done only after all child tasks are Done.

**Step 17:** Create a Bug.
- Board → **Create (+)** → select **Bug**: `Users are complaining that, they are getting multiple emails for password reset`
- Move: In progress → Done

**Step 18:** Open **Summary** tab.
*Expected:* Counts of completed / updated / created work items; Epic progress 50 %; after moving story to Done → Epic 100 %.

**Step 19:** Open **List** tab.
*Expected:* Tasks and status shown as a list.

**Step 20:** Open **Calendar** tab. Add an item with `+`.
*Expected:* Item goes to Backlog.

**Step 21:** Hover over **Project templates** options to view available templates.

**Step 22:** Create workflow status.
- Software Development project → right-side 3 dots → **Manage workflow**
- **Add status** → **Create new status**: `Deployed in Prod` → Add
- **Update workflow** → Save workflow for selected issues → select **Task, Subtask, Bug** → **Save & Continue**

**Step 23:** Go to project.
*Expected:* New column **Deployed in Prod** at the end of the board. Create task `Deployed Password Reset`.

**Step 24:** Releases.
- **Releases** → **Create version**
  - Name: `Password reset module v1.0`
  - Start date: `03.8.26`
  - Release date: `1.9.26`
  - Description: `Release date is on 1st Sept. 2026`
- **Save**; create one more version similarly.

*Expected:* Versions listed under Releases.

---

# Exp2 – Version Control using Git

**Step 1:** Create project folder.
```bash
mkdir example.com
cd example.com
ls
```
*Expected:* Empty directory.

**Step 2:** Create file.
```bash
vim calculator.sh
```
Type (`i` to insert), then `Esc` → `:wq`:
```bash
x=a+b
```
```bash
ls
```
*Expected:* `calculator.sh`

**Step 3:** Install Git.
```bash
apt-get install git
git
```
*Expected:* List of git commands/options displayed.

**Step 4:** Initialize repository.
```bash
git init
ls
ls -la
ls .git
```
*Expected:* `Initialized empty Git repository`; `.git` folder visible; `.git` contains `hooks`, `objects`, `refs`, `config`, etc.

**Step 5:** Check status.
```bash
git status
```
*Expected:* `Untracked files: calculator.sh` with suggestion to use `git add`.

**Step 6:** Track file.
```bash
git add calculator.sh
git status
```
*Expected:* `Changes to be committed: new file: calculator.sh`; no untracked files.

**Step 7:** Modify file.
```bash
clear
ls
vim calculator.sh
```
Change to:
```bash
x=a+b+c
```
```bash
git status
git diff
clear
```
*Expected:* `modified: calculator.sh`; `git diff` shows `-x=a+b` / `+x=a+b+c`.

**Step 8:** Configure identity and first commit.
```bash
vim calculator.sh
```
Set content:
```bash
x=a+b;
```
```bash
git config --global user.name "Sameer"
git config --global user.email "sstathare@git-india.edu.in"
git add calculator.sh
git commit -m "this is my first version of addition"
git status
```
*Expected:* `[main <id>] this is my first version of addition`; `On branch main – nothing to commit, working tree clean`.

**Step 9:** Second modification.
```bash
vim calculator.sh
```
Content:
```bash
x=a+b
y=a-b
```
```bash
cat calculator.sh
git status
```
*Expected:* `Changes not staged for commit: modified: calculator.sh`.

**Step 10:** Inspect and commit second version.
```bash
ls -la
ls .git/
ls .git/objects
ls
git status
git diff
git add calculator.sh
git status
git commit -m "this is my second version"
clear
```
*Expected:* `git diff` shows `+y=a-b`; commit created.

**Step 11:** View history.
```bash
git log
cat calculator.sh
```
*Expected:* Two commits with commit id, author, date/time; file shows both lines.

**Step 12:** Go back to first version.
```bash
git log
git reset --hard <paste first commit id>
cat calculator.sh
```
*Expected:* `HEAD is now at <id> this is my first version of addition`; file shows `x=a+b`.

**Step 13:** GitHub repository.
- Create GitHub account → Sign up
- GitHub icon → **New Repository**
- Repo name: `TE_Shell_Project`
- Description: `Shell scripting example`
- **Public**
- Check **Add a README file**
- **Create repository**

*Expected:* Repository page opens with README.md.

**Step 14:** Explore branching strategy.
- Open `https://github.com/kubernetes/kubernetes`
- Observe master branch, multiple feature branches, release branches (with version numbers)

---

# Exp3 – CI Pipeline using GitHub Actions

**Step 1:** Create GitHub account at `https://github.com`.

**Step 2:** Create repository.
- **New Repository** → Name: `CI-Pipeline-Demo` → **Public** → **Create Repository**

**Step 3:** Upload project: create file `index.html` → Commit.
```html
<!DOCTYPE html>
<html>
<head>
<title>CI Demo</title>
</head>
<body>
<h1>Continuous Integration using GitHub Actions</h1>
</body>
</html>
```

**Step 4:** Create workflow.
- **Actions** → **set up a workflow yourself**
*Expected:* GitHub creates `.github/workflows/main.yml`.

**Step 5:** Paste workflow and commit.
```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Display Welcome Message
        run: echo "Continuous Integration Started"

      - name: Display Current Directory
        run: pwd

      - name: List Repository Files
        run: ls

      - name: Display Completion Message
        run: echo "Pipeline Executed Successfully"
```

**Step 6:** Modify `index.html` – add:
```html
<h2>GitHub Actions Demo</h2>
```
Commit.
*Expected:* Workflow starts automatically. Actions tab: yellow circle (running) → green tick (success).

**Step 7:** View details: click **CI Pipeline** → click **build**.
*Expected:* Steps listed: Checkout Repository → Display Welcome Message → Display Current Directory → List Repository Files → Display Completion Message.

**Step 8:** Click each step to see console output.
*Expected:*
```
Continuous Integration Started
/home/runner/work/CI-Pipeline-Demo
index.html
README.md
Pipeline Executed Successfully
```

**Step 9:** Output meaning (reference)

| Output | Source |
|---|---|
| Checkout Repository | downloads files |
| pwd | current directory |
| ls | lists files |
| echo | prints message |

**Step 10:** Introduce an error – add this step to the workflow and commit.
```yaml
      - name: Invalid Command
        run: abcxyz
```
*Expected:* Workflow fails – red cross in Actions tab; error `abcxyz: command not found` in logs.

**Step 11:** Fix the error – replace with:
```yaml
      - name: Invalid Command
        run: echo "Error Fixed"
```
Commit.
*Expected:* Workflow succeeds – green tick.

---

# Exp4 – Ansible Provisioning & Configuration

**Step 1:** Open Ubuntu → Terminal (`Ctrl + Alt + T`).

**Step 2:** Update package list.
```bash
sudo apt update
```
*Expected:* Package lists downloaded/refreshed.

**Step 3:** Install Ansible.
```bash
sudo apt install ansible -y
```

**Step 4:** Verify.
```bash
ansible --version
```
*Expected:* `ansible [core x.x.x]` with config/python details.

**Step 5:** Create folder.
```bash
mkdir ansible-lab
cd ansible-lab
pwd
```
*Expected:* `/home/<user>/ansible-lab`

**Step 6:** Create inventory file.
```bash
nano inventory
```
Content:
```
localhost ansible_connection=local
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

Alternative (remote servers):
```
[servers]
192.168.10.20
192.168.10.21
```

**Step 7:** Test inventory.
```bash
ansible all -i inventory -m ping
```
*Expected:*
```
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

**Step 8:** Create playbook.
```bash
nano install_nginx.yml
```

**Step 9:** Write playbook.
```yaml
---
- hosts: localhost
  become: yes
  tasks:
    - name: Install Nginx Web Server
      apt:
        name: nginx
        state: present
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 10:** Execute playbook.
```bash
ansible-playbook -i inventory install_nginx.yml
```
*Expected:*
```
PLAY [localhost] ...
TASK [Gathering Facts] ... ok
TASK [Install Nginx Web Server] ... changed
PLAY RECAP
localhost : ok=2 changed=1 unreachable=0 failed=0
```
(Slide expects at least `changed=1`.)

**Step 11:** Verify installation.
```bash
nginx -v
systemctl status nginx
```
*Expected:* `nginx version: nginx/1.xx`; `Active: active (running)`.

**Step 12:** Open browser → `http://localhost`
*Expected:* "Welcome to nginx!" page.

---

# Exp5 – Docker Containerization

**Step 1:** Open Terminal (`Ctrl + Alt + T`).

**Step 2:** Check Docker.
```bash
docker --version
```
*Expected:* `Docker version xx.x.x, build ...`

**Step 3:** Check Docker service.
```bash
sudo systemctl status docker
```
*Expected:* `Active: active (running)`

If not running:
```bash
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
```

**Step 4:** Create project folder.
```bash
mkdir DockerLab
cd DockerLab
pwd
```
*Expected:* `/home/<user>/DockerLab`

**Step 5:** Create Python app.
```bash
nano app.py
```
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello Students! Welcome to Docker Lab."

app.run(host="0.0.0.0", port=5000)
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`
```bash
ls
```
*Expected:* `app.py`

**Step 6:** Create requirements file.
```bash
nano requirements.txt
```
```
Flask
```
Save and exit.
```bash
cat requirements.txt
```
*Expected:* `Flask`

**Step 7:** Create Dockerfile (no extension).
```bash
nano Dockerfile
```
```dockerfile
FROM python:3.11

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

EXPOSE 5000

CMD ["python","app.py"]
```
```bash
cat Dockerfile
```
*Expected:* Dockerfile content displayed.

**Step 8:** Check files.
```bash
ls
```
*Expected:* `app.py  Dockerfile  requirements.txt`

**Step 9:** Build image.
```bash
sudo docker build -t myapp .
```
*Expected:* `Successfully built <id>` / `Successfully tagged myapp:latest`

**Step 10:** Check images.
```bash
sudo docker images
```
*Expected:* `REPOSITORY: myapp` listed.

**Step 11:** Run container.
```bash
sudo docker run -d -p 5000:5000 --name mycontainer myapp
```
*Expected:* Long container ID printed.

**Step 12:** Check running containers.
```bash
sudo docker ps
```
*Expected:* `mycontainer` with status `Up`, port `0.0.0.0:5000->5000/tcp`.

**Step 13:** Open browser → `http://localhost:5000`
*Expected:* `Hello Students! Welcome to Docker Lab.`

**Step 14:** View logs.
```bash
sudo docker logs mycontainer
```
*Expected:* Flask startup messages (`Running on http://0.0.0.0:5000`) and request logs.

**Step 15:** Enter container.
```bash
sudo docker exec -it mycontainer bash
```
(If bash does not work: `sudo docker exec -it mycontainer sh`)
*Expected:* Prompt changes to `root@<container-id>:/app#`

**Step 16:** Verify files inside container.
```bash
ls
pwd
exit
```
*Expected:* `app.py  Dockerfile  requirements.txt` (slide shows `app.py requirements.txt`); `/app`

**Step 17:** Stop container.
```bash
sudo docker stop mycontainer
sudo docker ps
```
*Expected:* Container no longer listed.

**Step 18:** Start again.
```bash
sudo docker start mycontainer
sudo docker ps
```
*Expected:* `mycontainer` is `Up` again.

**Step 19:** Restart.
```bash
sudo docker restart mycontainer
```
*Expected:* `mycontainer` printed; container running.

**Step 20:** Remove container.
```bash
sudo docker stop mycontainer
sudo docker rm mycontainer
sudo docker ps -a
```
*Expected:* `mycontainer` not listed.

**Step 21:** Remove image.
```bash
sudo docker rmi myapp
sudo docker images
```
*Expected:* `Untagged: myapp:latest`; `myapp` no longer listed.

---

# Exp6 – Terraform: Create EC2 Instance on AWS

**Prerequisite:** Install Atom editor (`https://atom.io/`) or any editor; Terraform installed.

**Step 1:** Create working directory `C:\Terraform_Scripts`.

**Step 2:** Open Atom → **File → Open Folder** → select `Terraform_Scripts`.

**Step 3:** Create new file `EC2_on_Terraform`.

**Step 4:** Get AWS credentials.
- Open `https://aws.amazon.com/console` and log in
- Search **IAM** → **Users** → **Add users**
- User name: `Terraform_User`
- Access type: **Programmatic access** → **Next: Permissions**
- **Create group** → Group name: `Terraform_Group` → select policy **AdministratorAccess** → **Create group**
- Select the group → **Next: Tags**
- Tag: Key `Terraform`, Value `Access_Policy` (optional) → **Next: Review** → **Create user**
- Copy **Access key ID** and **Secret access key** (or **Download .csv**)

*Expected:* Success screen showing Access key ID and Secret access key.

**Step 5:** Get AMI ID.
- AWS Console → **EC2** → **Launch instance** → copy the AMI ID of the desired OS (note the region, e.g. `us-east-1`; AMI ids differ per region)

**Step 6:** Write script and save as `EC2_on_Terraform.tf`.
```hcl
provider "aws" {
  access_key = "<YOUR_ACCESS_KEY>"
  secret_key = "<YOUR_SECRET_KEY>"
  region     = "us-east-1"
}

resource "aws_instance" "terraform-ec2" {
  ami           = "<YOUR_AMI_ID>"
  instance_type = "t2.micro"
}
```

**Step 7:** Open Command Prompt.
```cmd
cd \
cd Terraform_Scripts
dir
```
*Expected:* `EC2_on_Terraform.tf` listed.

**Step 8:** Initialize.
```cmd
terraform init
```
*Expected:*
```
Initializing the backend...
Initializing provider plugins...
- Installing hashicorp/aws vX.XX.X...
Terraform has been successfully initialized!
```
(`.terraform.lock.hcl` created.)

**Step 9:** Plan.
```cmd
terraform plan
```
*Expected:* `+ resource "aws_instance" "terraform-ec2"` with `ami`, `instance_type = "t2.micro"`, many `(known after apply)`; `Plan: 1 to add, 0 to change, 0 to destroy.`

**Step 10:** Check EC2 dashboard before apply.
*Expected:* No running instances.

**Step 11:** Apply.
```cmd
terraform apply
```
Type `yes` when prompted.
*Expected:*
```
aws_instance.terraform-ec2: Creating...
aws_instance.terraform-ec2: Still creating... [10s elapsed]
...
aws_instance.terraform-ec2: Creation complete after 55s [id=i-xxxxxxxxxxxxxxxxx]
Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
```

**Step 12:** Check EC2 dashboard after apply.
*Expected:* One instance, state **Running**.

**Step 13:** Destroy.
```cmd
terraform destroy
```
Type `yes` when prompted.
*Expected:*
```
aws_instance.terraform-ec2: Destroying... [id=i-xxxxxxxxxxxxxxxxx]
aws_instance.terraform-ec2: Destruction complete after 48s
Destroy complete! Resources: 1 destroyed.
```

**Step 14:** Check EC2 dashboard after destroy.
*Expected:* Instance state **Terminated**.

---

# Exp7 (A) – Multi-Service Application using Docker Compose

**Step 1:** Install Docker Desktop.
1. Open Chrome → search **Docker Desktop** → download for Windows
2. Double-click `Docker Desktop Installer.exe` → **Yes**
3. Keep defaults, ensure **Use WSL 2 instead of Hyper-V** is ticked → **Install** (5–10 min)
4. **Restart computer**

**Step 2:** Start Docker Desktop.
*Expected:* Wait until status shows `Docker Engine Running`.

**Step 3:** Verify installation (Command Prompt / PowerShell).
```cmd
docker --version
docker compose version
```
*Expected:* `Docker version 28.x.x`; `Docker Compose version v2.x.x`

**Step 4:** Install VS Code (default settings) and open it once.

**Step 5:** Create folders.
```
Desktop
└── DockerLab
    └── compose-demo
```

**Step 6:** VS Code → **File → Open Folder** → select `compose-demo`.

**Step 7:** Create folders inside `compose-demo`: `app`, `nginx`.

**Step 8:** Create files.
```
compose-demo
│
├── docker-compose.yml
├── app
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt
└── nginx
    └── default.conf
```

**Step 9:** `app/app.py`
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "<h1>Hello from Docker Compose!</h1>"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

**Step 10:** `app/requirements.txt`
```
Flask
```

**Step 11:** `app/Dockerfile`
```dockerfile
FROM python:3.10

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python","app.py"]
```

**Step 12:** `nginx/default.conf`
```nginx
server {
    listen 80;

    location / {
        proxy_pass http://app:5000;
    }
}
```

**Step 13:** `docker-compose.yml`
```yaml
version: '3'

services:
  app:
    build: ./app
    container_name: flask_app

  nginx:
    image: nginx:latest
    container_name: nginx_server
    ports:
      - "80:80"
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - app
```

**Step 14:** Open terminal in VS Code (**Terminal → New Terminal**) and verify folder is `compose-demo`.
```cmd
cd path\to\compose-demo
```

**Step 15:** Build.
```cmd
docker compose build
```
*Expected:* Flask image built; ends with `Built` / `Image ... Built` (first build takes several minutes).

**Step 16:** Start.
```cmd
docker compose up
```
*Expected:* Network created; `flask_app` and `nginx_server` started; logs from both displayed.

**Step 17:** Verify (new terminal).
```cmd
docker ps
```
*Expected:*
```
CONTAINER ID   IMAGE     STATUS
abcd1234       flask_app Up
efgh5678       nginx     Up
```

**Step 18:** Browser → `http://localhost`
*Expected:* `Hello from Docker Compose!`

**Step 19:** Stop.
Press `Ctrl + C` or run:
```cmd
docker compose down
```
*Expected:* Containers and network removed.

---

# Exp7 (B) – Monitoring using Prometheus / Grafana / Nagios

## Part A – Prometheus

**Step 1:** Open Ubuntu terminal and update.
```bash
# Ctrl + Alt + T
sudo apt update
```

**Step 2:** Install utilities.
```bash
sudo apt install wget curl tar -y
```

**Step 3:** Create Prometheus user.
```bash
sudo useradd --no-create-home --shell /bin/false prometheus
```

**Step 4:** Create directories.
```bash
sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus
ls /etc/prometheus
```
*Expected:* Directory empty initially.

**Step 5:** Download the current Prometheus Linux release (from the official Prometheus site) for your architecture.
```bash
ls
```
*Expected:* `prometheus-x.x.x.linux-amd64.tar.gz`

**Step 6:** Extract.
```bash
tar -xvf prometheus-*.linux-amd64.tar.gz
cd prometheus-*.linux-amd64
ls
```
*Expected:* `prometheus  promtool  prometheus.yml  consoles  console_libraries`

**Step 7:** Install files.
```bash
sudo cp prometheus /usr/local/bin/
sudo cp promtool /usr/local/bin/
sudo cp prometheus.yml /etc/prometheus/
```

**Step 8:** Set ownership.
```bash
sudo chown -R prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo chown prometheus:prometheus /usr/local/bin/prometheus
sudo chown prometheus:prometheus /usr/local/bin/promtool
```

**Step 9:** Configure.
```bash
sudo nano /etc/prometheus/prometheus.yml
```
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 10:** Validate.
```bash
promtool check config /etc/prometheus/prometheus.yml
```
*Expected:* `SUCCESS: /etc/prometheus/prometheus.yml is valid prometheus config file syntax`

**Step 11:** Create service.
```bash
sudo nano /etc/systemd/system/prometheus.service
```
```ini
[Unit]
Description=Prometheus Monitoring
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/var/lib/prometheus

[Install]
WantedBy=multi-user.target
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 12:** Start Prometheus.
```bash
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus
```
*Expected:* `Active: active (running)`

**Step 13:** Browser → `http://localhost:9090`
*Expected:* Prometheus web UI opens.

**Step 14:** Open **Status → Targets**.
*Expected:* `prometheus` – `localhost:9090` – **UP**.

## Part B – Node Exporter

**Step 15:** Download current Node Exporter Linux release, then:
```bash
tar -xvf node_exporter-*.linux-amd64.tar.gz
cd node_exporter-*.linux-amd64
sudo cp node_exporter /usr/local/bin/
sudo useradd --no-create-home --shell /bin/false node_exporter
sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter
```

**Step 16:** Create service.
```bash
sudo nano /etc/systemd/system/node_exporter.service
```
```ini
[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 17:** Start Node Exporter.
```bash
sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter
```
*Expected:* `Active: active (running)`

**Step 18:** Browser → `http://localhost:9100/metrics`
*Expected:* Large text page with metrics such as `node_cpu_seconds_total`, `node_memory_MemTotal_bytes`, `node_memory_MemAvailable_bytes`, `node_filesystem_size_bytes`, `node_network_receive_bytes_total`.

**Step 19:** Add Node Exporter to Prometheus.
```bash
sudo nano /etc/prometheus/prometheus.yml
```
```yaml
global:
  scrape_interval: 15s

scrape_configs:

  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]

  - job_name: "node_exporter"
    static_configs:
      - targets: ["localhost:9100"]
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`
```bash
promtool check config /etc/prometheus/prometheus.yml
sudo systemctl restart prometheus
sudo systemctl status prometheus
```
*Expected:* Config valid; `Active: active (running)`.

**Step 20:** Open `http://localhost:9090` → **Status → Targets**.
*Expected:* Two targets – `prometheus` (`localhost:9090`) and `node_exporter` (`localhost:9100`) – both **UP**.

## Part C – Monitor CPU, Memory, Disk, Network

**Step 21:** In the Prometheus query page, run these metrics and use the **Graph** view:

| Resource | Query |
|---|---|
| CPU | `node_cpu_seconds_total` |
| Memory | `node_memory_MemAvailable_bytes` , `node_memory_MemTotal_bytes` |
| Disk | `node_filesystem_size_bytes` |
| Network | `node_network_receive_bytes_total` , `node_network_transmit_bytes_total` |

*Expected:* Time-series values shown and changing over time.

## Part D – Grafana

**Step 22:** Install Grafana (official Grafana repository/package for your Ubuntu version), then:
```bash
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
sudo systemctl status grafana-server
```
*Expected:* `Active: active (running)`

**Step 23:** Browser → `http://localhost:3000` → login `admin` / `admin` (set new password if asked).
*Expected:* Grafana home page.

**Step 24:** Connect data source.
- **Connections → Data Sources → Add data source** → **Prometheus**
- URL: `http://localhost:9090`
- **Save & Test**

*Expected:* "Successfully queried the Prometheus API" / data source connected.

**Step 25:** Create dashboard: **New Dashboard → Add Visualization** → select **Prometheus**. Create 4 panels:

| Panel | Title | Metrics to use |
|---|---|---|
| 1 | CPU Utilization | CPU metric (Time series or Gauge) |
| 2 | Memory Utilization | Node Exporter memory metrics |
| 3 | Disk Utilization | Filesystem metrics |
| 4 | Network Traffic | Network receive/transmit metrics |

Save dashboard as: `Linux System Monitoring`

*Expected:* Dashboard with CPU, Memory, Disk, Network graphs; graphs change when you perform normal computer activity.

## Part E – Nagios

**Step 26:** Install Nagios.
```bash
sudo apt install -y nagios4 nagios-plugins-contrib nagios-nrpe-plugin apache2
sudo systemctl status nagios4
```
*Expected:* `Active: active (running)`

**Step 27:** Create web admin user.
```bash
sudo htdigest -c /etc/nagios4/htdigest.users "Nagios4" nagiosadmin
```
*Expected:* Prompts to enter and confirm password.

**Step 28:** Enable authentication.
```bash
sudo nano /etc/nagios4/cgi.cfg
```
Ensure:
```
use_authentication=1
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`
```bash
sudo systemctl restart apache2
```

**Step 29:** Configure host and services.
```bash
sudo nano /etc/nagios4/objects/localhost.cfg
```
Host block:
```
define host {
    use         generic-host
    host_name   Ubuntu-Server
    alias       Ubuntu Local Host
    address     127.0.0.1
}
```
Services (add/verify at the bottom):
```
define service {
    use                  generic-service
    host_name            Ubuntu-Server
    service_description  HTTP
    check_command        check_http
}

define service {
    use                  generic-service
    host_name            Ubuntu-Server
    service_description  SSH
    check_command        check_ssh
}

define service {
    use                  generic-service
    host_name            Ubuntu-Server
    service_description  Root Partition Disk
    check_command        check_local_disk!-w 20% -c 10% -p /
}
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 30:** Validate and restart.
```bash
sudo nagios4 -v /etc/nagios4/nagios.cfg
sudo systemctl restart nagios4
sudo systemctl status nagios4
```
*Expected:* `Total Warnings: 0`, `Total Errors: 0`; service `active (running)`.

**Step 31:** Open dashboard.
- Browser → `http://localhost/nagios4` (or `http://<SERVER_IP>/nagios4`)
- Login: `nagiosadmin` + password from Step 27
- Left pane → **Hosts** / **Services**

*Expected:* `Ubuntu-Server` = **UP**; HTTP, SSH, Root Partition Disk = **OK** (green).

**Step 32:** Test 1 – HTTP alert (only on isolated lab VM).
```bash
sudo systemctl stop apache2
```
Refresh Nagios dashboard.
*Expected:* HTTP: OK → **CRITICAL** (red).
```bash
sudo systemctl start apache2
```
*Expected:* HTTP: CRITICAL → **OK**.

**Step 33:** Test 2 – SSH alert.
```bash
sudo systemctl stop ssh
```
*Expected:* SSH: OK → **CRITICAL**.
```bash
sudo systemctl start ssh
```
*Expected:* SSH restored to **OK**.

---

# Exp9 – Kubernetes on Ubuntu (Minikube)

## Part A – Prepare Ubuntu

**Step 1:** Open terminal: `Ctrl + Alt + T`

**Step 2:**
```bash
sudo apt update
```
*Expected:* Package lists refreshed.

## Part B – Install Docker

**Step 3:** Check Docker.
```bash
docker --version
```
*Expected:* `Docker version 28.x.x` (if installed; otherwise continue).

**Step 4:** Install Docker.
```bash
sudo apt install docker.io -y
```

**Step 5:**
```bash
sudo systemctl start docker
```

**Step 6:**
```bash
sudo systemctl enable docker
```

**Step 7:**
```bash
sudo systemctl status docker
```
*Expected:* `Active: active (running)`. Press `q` to exit.

## Part C – Install kubectl

**Step 10:**
```bash
sudo snap install kubectl --classic
```

**Step 11:**
```bash
kubectl version --client
```
*Expected:* `Client Version: v1.xx.x`

## Part D – Install Minikube

**Step 13:**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

**Step 14:**
```bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

**Step 15:**
```bash
minikube version
```
*Expected:* `minikube version: v...`

## Part E – Start Cluster

**Step 16:**
```bash
minikube start --driver=docker
```
*Expected:* Cluster started successfully message (first run takes a few minutes).

**Step 17:**
```bash
minikube status
```
*Expected:*
```
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

## Part F – Check Cluster

**Step 18:**
```bash
kubectl cluster-info
```
*Expected:* Kubernetes control plane URL displayed.

**Step 19:**
```bash
kubectl get nodes
```
*Expected:*
```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   ...   ...
```

## Part G – Deploy Application

**Step 20:** Create deployment.
```bash
kubectl create deployment nginx --image=nginx
```
*Expected:* `deployment.apps/nginx created`

**Step 21:**
```bash
kubectl get deployments
```
*Expected:*
```
NAME    READY   UP-TO-DATE   AVAILABLE
nginx   1/1     1            1
```

**Step 22:**
```bash
kubectl get pods
```
*Expected:*
```
NAME                     READY   STATUS    RESTARTS   AGE
nginx-xxxxxxxxxx-xxxxx   1/1     Running   0          ...
```

**Step 23:** Relationship (reference): Deployment → ReplicaSet → Pod → Nginx container.

## Part H – Examine Pod

**Step 24:**
```bash
kubectl get pods
kubectl describe pod <pod-name>
```
Example: `kubectl describe pod nginx-7c5ddbdf54-abcde`
*Expected:* Pod name, namespace, node, container, image, IP, events, status.

**Step 25:**
```bash
kubectl describe deployment nginx
```
*Expected:* Deployment details.

## Part I – Expose Application

**Step 26:**
```bash
kubectl expose deployment nginx --type=NodePort --port=80
```
*Expected:* `service/nginx exposed`

**Step 27:**
```bash
kubectl get services
```
*Expected:*
```
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)
kubernetes   ClusterIP   ...          <none>        443/TCP
nginx        NodePort    ...          <none>        80:xxxxx/TCP
```

## Part J – Access Application

**Step 28:**
```bash
minikube service nginx
```
*Expected:* Service URL shown; browser opens with **Welcome to nginx!**

## Part K – Scale Up

**Step 30:**
```bash
kubectl get pods
```
*Expected:* 1 Pod.

**Step 31:**
```bash
kubectl scale deployment nginx --replicas=3
```
*Expected:* `deployment.apps/nginx scaled`

**Step 32:**
```bash
kubectl get pods
```
*Expected:* 3 Pods in `Running` state.

## Part L – Scale Down

**Step 33:**
```bash
kubectl scale deployment nginx --replicas=2
kubectl get pods
```
*Expected:* 2 Pods.

## Part M – Logs

**Step 34:**
```bash
kubectl get pods
```

**Step 35:**
```bash
kubectl logs <pod-name>
```
Example: `kubectl logs nginx-xxxxxxxxxx-xxxxx`
*Expected:* Container log output (nginx startup messages).

## Part N – Execute Command in Container

**Step 36:**
```bash
kubectl exec -it <pod-name> -- /bin/bash
```
*Expected:* Prompt changes, e.g. `root@nginx-container:/#`

**Step 37:** Inside the container:
```bash
ls
pwd
```
*Expected:* Root file system listing; `/`

**Step 38:**
```bash
exit
```
*Expected:* Back to Ubuntu prompt.

## Part O – Update Deployment

**Step 39:**
```bash
kubectl get deployment nginx -o wide
```
*Expected:* Image column shows `nginx`.

## Part P – Self-Healing

**Step 40:**
```bash
kubectl get pods
```

**Step 41:**
```bash
kubectl delete pod <pod-name>
```
Example: `kubectl delete pod nginx-xxxxxxxxxx-xxxxx`
*Expected:* `pod "nginx-xxxxxxxxxx-xxxxx" deleted`

**Step 42:**
```bash
kubectl get pods
```
*Expected:* A new Pod is created automatically; desired replica count maintained.

## Part Q – All Resources

**Step 43:**
```bash
kubectl get all
```
*Expected:* Pods, `service/nginx NodePort`, `deployment.apps/nginx 2/2`, `replicaset.apps/nginx-xxxxxxxx` (desired 2).

## Part R – Dashboard

**Step 44:**
```bash
minikube dashboard
```
*Expected:* Browser opens with Kubernetes dashboard (Nodes, Namespaces, Workloads, Services).

## Part S – Clean Up

**Step 45:**
```bash
kubectl delete service nginx
```
*Expected:* `service "nginx" deleted`

**Step 46:**
```bash
kubectl delete deployment nginx
```
*Expected:* `deployment.apps "nginx" deleted`

**Step 47:**
```bash
kubectl get all
```
*Expected:* Only `service/kubernetes` remains; nginx resources gone.

## Part T – Stop Minikube

**Step 48:**
```bash
minikube stop
```
*Expected:* Node stopped message.

## Part U – (Optional) Delete Cluster
```bash
minikube delete
```
*Expected:* Minikube cluster removed.

---

# Exp10 – ML Lifecycle with MLflow

**Step 1:** Create project folder and check tools.
```bash
mkdir mlflow_experiment
cd mlflow_experiment
python3 --version
pip3 --version
```
*Expected:* Python 3.x.x and pip version displayed.

**Step 2:** Create and activate virtual environment.
```bash
python3 -m venv venv
source venv/bin/activate
```
*Expected:* Prompt shows `(venv) user@ubuntu:~/mlflow_experiment$`

**Step 3:** Install packages.
```bash
pip install mlflow scikit-learn pandas
mlflow --version
```
*Expected:* `mlflow, version x.x.x`

**Step 4:** Start MLflow server in a **second terminal** (leave it open).
```bash
cd ~/mlflow_experiment
source venv/bin/activate
mlflow server --port 5000
```
*Expected:* `Uvicorn running on http://127.0.0.1:5000`

**Step 5:** Browser → `http://localhost:5000`
*Expected:* MLflow UI opens.

**Step 6:** In the **first terminal**, create `train_model.py`.
```bash
nano train_model.py
```
```python
import mlflow
import mlflow.sklearn
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# Connect Python program to MLflow Tracking Server
mlflow.set_tracking_uri("http://localhost:5000")

# Create/select experiment
mlflow.set_experiment("Iris_ML_Lifecycle")

# Load Iris dataset
iris = load_iris()
X = iris.data
y = iris.target

# Divide data into training and testing data
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

# Start MLflow run
with mlflow.start_run() as run:

    # Model parameters
    max_iter = 200

    # Create machine learning model
    model = LogisticRegression(max_iter=max_iter)

    # Train model
    model.fit(X_train, y_train)

    # Make predictions
    y_pred = model.predict(X_test)

    # Calculate accuracy
    accuracy = accuracy_score(y_test, y_pred)

    # Log parameters
    mlflow.log_param("algorithm", "Logistic Regression")
    mlflow.log_param("max_iter", max_iter)
    mlflow.log_param("test_size", 0.2)

    # Log metric
    mlflow.log_metric("accuracy", accuracy)

    # Log and register model
    mlflow.sklearn.log_model(
        sk_model=model,
        name="iris_model",
        registered_model_name="Iris_Logistic_Regression"
    )

    print("Model training completed.")
    print("Accuracy:", accuracy)
    print("Run ID:", run.info.run_id)

print("Experiment completed successfully.")
```
Save: `Ctrl+O` → `Enter` → `Ctrl+X`

**Step 7:** Run.
```bash
python train_model.py
```
*Expected:*
```
Model training completed.
Accuracy: 1.0
Run ID: xxxxxxxxxxxxxxxxxxxxx
Experiment completed successfully.
```
(Accuracy may vary slightly depending on version/data split.)

**Step 8:** Observe MLflow UI.
- `http://localhost:5000` → open **Iris_ML_Lifecycle** → click the run

*Expected:*
- Parameters: `algorithm = Logistic Regression`, `max_iter = 200`, `test_size = 0.2`
- Metric: `accuracy`
- Model: `iris_model`
- Run ID shown

**Step 9:** Model registration.
- MLflow UI → **Models** → `Iris_Logistic_Regression`

*Expected:* `Version 1` listed.

**Step 10:** Load registered model. Create `predict.py`.
```bash
nano predict.py
```
```python
import mlflow

mlflow.set_tracking_uri("http://localhost:5000")

model = mlflow.pyfunc.load_model("models:/Iris_Logistic_Regression/1")

prediction = model.predict([[5.1, 3.5, 1.4, 0.2]])

print("Prediction:", prediction)
```
Save and run:
```bash
python predict.py
```
*Expected:* `Prediction: [0]`  (0 = Setosa, 1 = Versicolor, 2 = Virginica)

**Step 11:** Deploy model – open a **third terminal**.
```bash
cd ~/mlflow_experiment
source venv/bin/activate
mlflow models serve \
-m "models:/Iris_Logistic_Regression/1" \
-p 5001
```
*Expected:* Model server starts and listens on `http://127.0.0.1:5001`. Keep terminal open.

**Step 12:** Test deployed model – open a **fourth terminal**.
```bash
curl -X POST http://127.0.0.1:5001/invocations \
-H "Content-Type: application/json" \
-d '{"inputs": [[5.1, 3.5, 1.4, 0.2]]}'
```
*Expected:* Response containing prediction `[0]` (Setosa).
