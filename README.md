# how-to-download-Lennix-and-ROS
step by step upload


## Part 1: Install Linux (via WSL)

# Step 1 — Open PowerShell as Administrator
Right-click the Start menu → "Windows PowerShell (Admin)" or "Terminal (Admin)".
Why: Installing WSL changes system-level Windows features, so it needs admin rights.

# Step 2 —Install WSL and Ubuntu
wsl --install

Why: This single command enables the WSL feature, downloads the Linux kernel, and installs Ubuntu (the default distro) automatically.

# Step 3 — Restart your computer
Why: Windows needs to finish enabling the virtualization features before Linux can run.

# Step 4 — Launch Ubuntu and set up your user account
Open "Ubuntu" from the Start menu, then create a username and password when prompted.
Why: This is your Linux user account, separate from your Windows account — it's needed to run commands with sudo.

# Step 5 — Update Ubuntu's package list

sudo apt update && sudo apt upgrade -y

Why: This makes sure your Linux system has the latest package information before you install anything else, avoiding version conflicts.

## Part 2: Install ROS

# Step 6 — Set up your ROS repository sources

sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Why: By default, Ubuntu doesn't know where to find ROS packages — this tells it to look at the official ROS package server.

# Step 7 — Add the ROS key

sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

Why: This key verifies that the packages you download actually come from the official ROS source and haven't been tampered with.

# Step 8 — Update package list again

sudo apt update

Why: Now that Ubuntu knows about the ROS repository, this refreshes the list so ROS packages become visible/installable.

## Step 9 — Install ROS (full desktop version)

sudo apt install ros-noetic-desktop-full

Why: This installs ROS itself, plus common tools like simulators and visualization software, in one go.

# Step 10 — Set up environment variables

echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc

Why: This tells your terminal where ROS is installed every time you open it, so you can run ROS commands without extra setup.

# Step 11 — Verify installation

roscore

Why: This starts the ROS master process — if it runs without errors, your installation was successful.
