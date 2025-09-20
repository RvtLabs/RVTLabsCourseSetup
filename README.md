# Exercises 0 - Setup

Complete setup guide from machine preparation to ready-to-use ROS 2 environment.

## What is Ubuntu and Why Do We Need It?

### What is Ubuntu?
**Ubuntu** is a free, open-source Linux-based operating system that serves as the standard platform for robotics development. It provides:
- **User-friendly**: Easy to install and use, accessible for beginners
- **Professional-grade**: Stable and reliable for development and production
- **Open source**: Free to use with strong community support
- **Hardware compatible**: Works on most modern computers

### Why Ubuntu for ROS 2 and Robotics?

- **🤖 Industry Standard**: 90% of robotics companies and universities use Ubuntu/Linux
- **🔧 Native Performance**: ROS 2 runs optimally on Ubuntu with direct hardware access
- **📦 Easy Installation**: One-command software installation via `apt` package manager
- **🌐 Large Community**: Extensive documentation, tutorials, and support ecosystem
- **💡 Development Tools**: Native C++/Python support and robotics-optimized tools

### Ubuntu vs Other Operating Systems

| Feature | Ubuntu | Windows | macOS |
|---------|--------|---------|-------|
| ROS 2 Support | ✅ Native | ⚠️ Limited/WSL | ⚠️ Limited |
| Performance | ✅ Optimal | ❌ Overhead | ❌ Limited |
| Cost | ✅ Free | ❌ Licensed | ❌ Hardware Cost |
| Robotics Ecosystem | ✅ Complete | ⚠️ Partial | ⚠️ Partial |

### Windows vs Ubuntu (Quick Comparison)

- **Windows**: Familiar interface, requires WSL for ROS 2, paid licensing
- **Ubuntu**: Developer-focused, native ROS 2 support, completely free
- **For Robotics**: Ubuntu is industry standard with better performance and tooling

## Step 1: Machine Requirements

**Hardware Prerequisites:**
- Intel or AMD processor (x64 architecture)
- Minimum 8GB RAM (16GB recommended)
- Minimum 50GB free storage
- Graphics card with OpenGL support (for Gazebo simulation)
- Stable internet connection

## Step 2: Ubuntu 22.04 Installation

**Why Ubuntu 22.04 and ROS 2 Humble?**
- **Long Term Support**: ROS 2 Humble LTS has official support until May 2027
- **Proven Stability**: Ubuntu 22.04 + Humble is the most tested combination
- **Educational Focus**: Best choice for learning robotics fundamentals


Choose the best option for your situation:

### Option A: Dual Boot (Recommended for Performance)
1. **Backup** your current system
2. **Download** Ubuntu 22.04.5 LTS from [Ubuntu Releases](https://releases.ubuntu.com/jammy/)
   - Download: `ubuntu-22.04.5-desktop-amd64.iso` (4.4GB)
3. **Create** bootable USB using Rufus (Windows) or Etcher (Mac/Linux)
4. **Install** Ubuntu alongside your existing OS
5. **Pros**: Native performance, full hardware access
6. **Cons**: Requires restart to switch between OS

### Option B: Virtual Machine (Easiest Setup)
1. **Install** virtualization software:
   - VMware Workstation (recommended)
   - VirtualBox (free alternative)
   - Parallels (Mac)
2. **Download** Ubuntu 22.04.5 LTS ISO from [Ubuntu Releases](https://releases.ubuntu.com/jammy/)
   - Download: `ubuntu-22.04.5-desktop-amd64.iso` (4.4GB)
3. **Configure** VM with:
   - **RAM**: 8GB minimum (more if available)
   - **Storage**: 50GB minimum
   - **CPU**: 4+ cores if available
4. **Install** Ubuntu 22.04 in VM
5. **Pros**: Safe, easy to remove, run alongside current OS
6. **Cons**: Reduced performance, resource sharing

### Option C: Native Installation (Best Performance)
1. **Backup** all important data
2. **Download** Ubuntu 22.04.5 LTS from [Ubuntu Releases](https://releases.ubuntu.com/jammy/)
   - Download: `ubuntu-22.04.5-desktop-amd64.iso` (4.4GB)
3. **Replace** existing OS completely with Ubuntu 22.04
4. **Pros**: Maximum performance
5. **Cons**: Removes existing operating system

## Step 3: ROS 2 Humble Installation

Once Ubuntu 22.04 is running:

1. **Follow the complete guide**: [ROS 2 Humble Installation Guide](ROS2%20Installation%20Guide.md)
2. **Install Desktop version** (includes RViz, demos, tutorials)
3. **Verify installation** with the examples below

### Verification: Talker-Listener Test

If you installed `ros-humble-desktop`, you can try some examples to verify your installation.

**In one terminal, run a C++ talker:**
```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp talker
```

**In another terminal, run a Python listener:**
```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_py listener
```

You should see the talker saying that it's Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly.

## Troubleshooting

- **Gazebo won't start**: Check graphics drivers and system specs
- **Build errors**: Ensure all dependencies installed correctly
- **Performance issues**: Consider increasing VM resources or using dual boot

## Next Steps

✅ **Setup Complete!** → Stay Tunned more updates comming soon..
