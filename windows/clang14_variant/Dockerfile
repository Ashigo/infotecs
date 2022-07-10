FROM mcr.microsoft.com/windows/servercore/iis

ENV DIR=openssl

# Add chocolatey repo && install packages %% add to the %PATH%
RUN powershell Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
RUN choco install visualstudio2022buildtools llvm git strawberryperl nasm cmake -y
RUN setx /M PATH "%PATH%;C:\Program Files\NASM;C:\Program Files\CMake\bin"

# Clone openssl repo && Checkout to 1.1.1 branch
RUN git clone https://github.com/openssl/openssl.git
WORKDIR ${DIR}
RUN git config —global —add safe.directory C:/openssl
RUN git checkout -b OpenSSL_1_1_1-stable origin/OpenSSL_1_1_1-stable

# Add env variables for C and C++ compilers
RUN powershell $env:CC='C:\Program Files\LLVM\bin\clang.exe'
RUN powershell $env:CXX='C:\Program Files\LLVM\bin\clang++.exe'
# RUN setx /M PATH "%PATH%;C:\Program Files (x86)\Microsoft Visual Studio\Installer"

RUN CMD vcvarsall.bat amd64
RUN perl Configure VC-WIN64A
RUN nmake
RUN nmake test

CMD [ "cmd.exe" ]