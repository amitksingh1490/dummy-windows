# Use a Windows Server Core base image with .NET Framework 4.8
FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

# Install Node.js
RUN Invoke-WebRequest -Uri "https://nodejs.org/dist/v14.17.0/node-v14.17.0-x64.msi" -OutFile "nodejs.msi" -UseBasicParsing ; \
    Start-Process -FilePath "nodejs.msi" -ArgumentList "/quiet" -Wait ; \
    Remove-Item -Force "nodejs.msi"

# Set up environment variables for Node.js and npm
ENV PATH="C:\\Program Files\\nodejs;${PATH}"

# Check node and npm versions
RUN node --version ; \
    npm --version

# Create a working directory
WORKDIR C:/workspace
