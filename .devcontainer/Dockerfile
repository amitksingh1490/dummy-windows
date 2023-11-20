# Use Windows Server Core as a base image
FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Set shell to PowerShell for convenience
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]

# Install Chocolatey - a package manager for Windows
RUN Set-ExecutionPolicy Bypass -Scope Process -Force; \
    [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; \
    iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Install necessary tools and languages using Chocolatey
RUN choco install -y git nodejs-lts openjdk11 go curl wget

# Install Build Tools for C++ (Visual Studio Build Tools)
RUN choco install -y visualstudio2019buildtools --package-parameters "--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64"

# Set up environment variables
ENV JAVA_HOME="C:\Program Files\OpenJDK\openjdk-11"
ENV PATH="${JAVA_HOME}\bin;${PATH}"

# Set up Go environment variables
ENV GOROOT="C:\Go"
ENV GOPATH="C:\go-work"
ENV PATH="${GOROOT}\bin;${GOPATH}\bin;${PATH}"

# Create a workspace directory
RUN New-Item -ItemType directory -Path C:\workspace
WORKDIR C:\workspace

# Expose necessary ports
EXPOSE 8000 3000
