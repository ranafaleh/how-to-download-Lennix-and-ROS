# how-to-download-Lennix-and-ROS
step by step upload



## Part 1: Enable WSL and Install Ubuntu

# Step 1
— Open PowerShell as Administrator
Right-click the Start menu → "Windows PowerShell (Admin)"
Why: Enabling WSL changes system-level settings, so it requires administrator rights.

#Step 2 
Install Ubuntu 22.04

wsl --install -d Ubuntu-22.04

Why: This command enables WSL and downloads Ubuntu 22.04 specifically (instead of the default version), because ROS2 Humble requires exactly this Ubuntu version.

After this, restart your computer, then open Ubuntu and set up a username and password.

## Part 2: Install ROS2 Humble

# Step 3 — Update the system

sudo apt update && sudo apt upgrade

Why: This updates the package list and installed programs before adding anything new, to avoid compatibility issues.

# Step 4 — Install essential tools

sudo apt install software-properties-common curl

Why: These are helper tools — curl is used to download files from the internet, and software-properties-common lets Ubuntu handle additional software sources (not just the default ones).

# Step 5 — Download the ROS authentication key

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

Why: This key verifies that the packages we're about to download actually come from the official ROS source and haven't been tampered with.

# Step 6 — Add the ROS2 repository

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

Why: By default, Ubuntu doesn't know where to find ROS2 packages — this line adds the official ROS2 repository address for Ubuntu 22.04 (codename "jammy").

# Step 7 — Update the package list again

sudo apt update

Why: Now that the ROS2 repository has been added, this refreshes the list so the system can see the available ROS2 packages.

# Step 8 — Install ROS2 Humble

sudo apt install ros-humble-desktop

Why: This installs ROS2 itself along with its core tools (simulation, visualization, etc.) in a single command.

Part 3: Run and Verify ROS2

# Step 9 — Automatically link ROS2 to the terminal

echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc

Why: This makes the terminal automatically recognize ROS2 commands every time you open it, instead of typing the command manually each time.

# Step 10 — Verify the installation

ros2 --version
echo $ROS_DISTRO

Why: The first command confirms ROS2 is installed and working, and the second prints the distro name (it should say "humble") as proof everything is set up correctly.
