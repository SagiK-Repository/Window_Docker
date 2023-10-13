문서정보 : 2023.10.13.~ 작성, 작성자 [@SAgiKPJH](https://github.com/SAgiKPJH)

<br>

# Window_Docker
Window Docker 전격 분석

### 목표
- [ ] Window Docker 문서 분석
  - [x] Windows 기반 컨테이너 설명서
    - [x] 시작하기
      - [x] 환경설정

### 제작자
[@SAgiKPJH](https://github.com/SAgiKPJH)

<br><br>

---

<br><br>

# Window Docker 문서 분석

## Windows 기반 컨테이너 설명서

- 링크 : https://learn.microsoft.com/ko-kr/virtualization/windowscontainers/
- Window 기반 컨테이너에 대한 제공 가이드.
  - 주요 콘텐츠
  - 개요
  - 시작하기
  - 자습서
  - 개념
  - 참고

<br>

### 시작하기

#### 요약

- 환경설정
  - 기본적인 docker desktop이 동작 가능하면 충분합니다.
  - 추가로 Window Admin Center를 통해 Window Docker를 다룰 수 있습니다.

<br>

#### 본문

<details><summary>Step 1/summary>

### 시작하기 Step1. 환경설정

#### 필수 구성 요소

- 링크 : [시작: 컨테이너에 맞게 Windows 준비](https://learn.microsoft.com/ko-kr/virtualization/windowscontainers/quick-start/set-up-environment?tabs=dockerce)
- 환경 조건
  1. 업데이트(버전 1607) 이상이 적용된 Windows 10 또는 11 Professional 또는 Enterprise를 실행하는 PC가 있어야 합니다.
  2. Hyper-V 사용하도록 설정되어 있어야 합니다.
- Test Window 파일
  - [Window Server 2022 Evaluation](https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-server-2022)
  - [Windows Server Insider Preview](https://www.microsoft.com/en-us/windowsinsider/for-business-getting-started-server)
- Azure VM Container-Ready
  - Azure Kubernetes Service를 통한 End-To-End 환경을 제공합니다.
  - [AKS에서 Windows로 시작](https://learn.microsoft.com/ko-kr/azure/aks/learn/quick-windows-container-deploy-cli?tabs=add-windows-node-pool)
  - [AKS-HCI에서 Windows로 시작](https://learn.microsoft.com/ko-kr/azure/aks/hybrid/kubernetes-walkthrough-powershell)
  - [Azure VM Image Builder를 사용하여 Windows VM 만들기](https://learn.microsoft.com/ko-kr/azure/virtual-machines/windows/image-builder)

<br>

#### 컨테이너 런타임 설치

1. [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) 설치
2. 기본 컨테이너 유형을 Windows 컨테이너로 변경합니다.  
   ```console
   # console
   $Env:ProgramFiles\Docker\Docker\DockerCli.exe -SwitchDaemon .
   ```  
   - 또는 Window 작업표시줄 -> docker 아이콘 -> 오른쪽 마우스 -> `Switch to Windows containers...` 클릭
3. [Windows Admin Center](https://learn.microsoft.com/ko-kr/windows-server/manage/windows-admin-center/overview)를 [다운로드](https://www.microsoft.com/ko-kr/evalcenter/download-windows-admin-center)합니다.
4. Windows Admin Center를 사용하여 Windows Server 머신을 컨테이너 호스트로 올바르게 설정
   - Windows Admin Center 인스턴스에 최신 컨테이너 확장이 설치
   - 실행시 바로 나타나는 Install 버튼 클릭
5. 다음 화면이 나타나야 합니다.  
   <img src="https://learn.microsoft.com/ko-kr/virtualization/windowscontainers/quick-start/media/wac-images.png"/>  
6. Window Container를 실행하려면 지원되는 런타임 [Containerd](https://kubernetes.io/docs/setup/production-environment/container-runtimes/#containerd), [Moby](https://mobyproject.org/) 및 [Mirantis Container Runtime](https://www.mirantis.com/try-mcr/)를 활용해야 합니다.
   - Docker CE/Mody
     ```powershell
     # powershell
     Invoke-WebRequest -UseBasicParsing "https://raw.githubusercontent.com/microsoft/Windows-Containers/Main/helpful_tools/Install-DockerCE/install-docker-ce.ps1" -o install-docker-ce.ps1
     .\install-docker-ce.ps1
     ```
   - Mirantis Container Runtime [지침참고](https://www.mirantis.com/software/mirantis-container-runtime/)
   - Containerd
     ```powershell
     # powershell
     Invoke-WebRequest -UseBasicParsing "https://raw.githubusercontent.com/microsoft/Windows-Containers/Main/helpful_tools/Install-ContainerdRuntime/install-containerd-runtime.ps1" -o install-containerd-runtime.ps1
     .\install-containerd-runtime.ps1
     ```

</details>
