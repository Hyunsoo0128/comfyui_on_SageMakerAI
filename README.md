# ComfyUI on Amazon SageMaker AI Studio
이 저장소는 Amazon SageMaker AI Studio에서 ComfyUI를 설치하고 실행하는 방법을 안내합니다.

## 목차
1. [SageMaker AI Studio 환경 설정](#step-1-amazon-sagemaker-ai-studio-환경-설정)
2. [ComfyUI 설치 및 환경 설정](#step-2-주피터랩-스페이스에서-comfyui-설치-및-환경-설정)
3. [ComfyUI 기동 및 접속](#step-3-comfyui-기동-및-접속)
4. [ComfyUI 워크플로 불러오기 및 GUI 초기 설정](#step-4-comfyui-워크플로-불러오기-및-gui-초기-설정)
5. [ComfyUI 워크플로 실행하기](#step-5-comfyui-워크플로-실행하기)

## Step 1. Amazon SageMaker AI Studio 환경 설정
AWS Management Console에 접속하여, SageMaker AI 선택 --> SageMaker Studio
SageMaker Studio 콘솔 화면에서 하기 그림과 같이 주피터랩 스페이스를 생성한다.
* 이미지 생성 모델 구동을 위해 GPU 탑재 인스턴스를 선택해야 함. (추천 ml.g5.2xlarge)
* 복수 모델을 다운로드하여 사용하기 위해 충분한 스토리지를 확보해야 함. (100GB 상당)
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/1.png" />

## Step 2. 주피터랩 스페이스에서 ComfyUI 설치 및 환경 설정
아래 그림과 같이 SageMaker Studio 콘솔 화면에서 Open JupyterLab을 클릭하여 작업 스페이스를 연다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/2.png" />

하기 그림과 같이 Github Repository의 코드 파일을 스페이스 내에 복제한다.
Git Repositories URL에 하기 주소를 입력한다.
https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI.git
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/3.png" />

복제된 코드 파일 가운데 ComfyUI_ModelPrep.ipynb를 선택한다.
우측 상단에서 올바른 커널을 선택한 후, 모든 셀을 자동 실행시킨다. 
본 파일에서는 ComfyUI 설치 및 환경 설정을 실행 한 후, 필수 AI 모델을 다운로드한다.
모든 셀의 동작이 완전히 완료된 후 다음 단계로 넘어간다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/4.png" />
* 복제된 프로젝트 폴더 내에 존재하는 "/workflow_temp"와 "/input_img" 두개 폴더를 로컬 컴퓨터에 다운로드한다.
* "/workflow_temp"에는 미리 작성한 comfyUI 워크플로 예제가 저장되어 있으며, "/input_img"에는 워크플로 예제에서 사용하기 위한 이미지 파일이 저장되어 있다.

## Step 3. ComfyUI 기동 및 접속
이어서, ComfyUI_Start.ipynb를 선택한다.
우측 상단에서 올바른 커널을 선택한 후, 모든 셀을 자동 실행시킨다.
이를 통해, ComfyUI가 백그라운드에서 실행된다.
https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI.git
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/5.png" />

아래 그림과 같은 문구가 주피터노트북 화면에 표시되면 ComfyUI에 접속이 가능하다.
현재 JupyterLab을 사용 중인 웹 브라우저의 주소창을 확인합니다. 
아래와 비슷한 형태일 것입니다.
https://<스튜디오-ID>.studio.<리전>.sagemaker.aws/jupyter/default/lab
기본 URL 추출 위 주소에서 /lab 부분을 제외한 앞부분을 복사한 후, 뒤에 /proxy/8188/을 붙여 웹 브라우저의 주소창에 입력한다.
https://<스튜디오-ID>.studio.<리전>.sagemaker.aws/jupyter/default/proxy/8188/
* 상기 URL의 가장 마지막에 꼭 '/' 기호가 들어가야 함을 잊지 말자. 
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/6.png" />

## Step 4. ComfyUI 워크플로 불러오기 및 GUI 초기 설정
웹 브라우저를 통해 ComfyUI에 접속하면 하기와 같은 초기 화면이 나타난다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/7.png" />

상단 메뉴바에서 워크플로를 클릭한 후, 열기를 클릭하여 사전에 공유된 워크플로 파일을 불러온다.
* 로컬 컴퓨터에 다운로드한 "/workflow_temp" 폴더 내의 워크플로 파일을 선택한다.
* 본 예제에서는 item_with_bg_beta.json 파일을 선택하였음. 
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/8.png" />
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/9.png" />

워크플로를 불러오면, 미설치된 노드에 대한 알림이 하기 그림과 같이 표시된다.
ComfyUI-IPAdapter_plus
WAS Node Suite (Revised)
ComfyUI's ControlNet Auxiliary Preprocessors
ComfyUI Manager를 열어 상기 세개의 노드팩을 모두 설치한다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/10.png" />
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/11.png" />

노드팩이 모두 설치되면, 하단에 재기동 버튼이 생성된다.
재기동 버튼을 클릭하여 ComfyUI를 다시 시작한다.
그리고, 주소창을 통해 재접속한다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/12.png" />

그리고, 주소창을 통해 재접속한다.
ComfyUI의 GUI 화면에 워크플로가 정상적으로 로드된 것을 확인할 수 있다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/13.png" />

## Step 5. ComfyUI 워크플로 실행하기
좌측 세개의 이미지 로더 노드를 통해 상품 이미지, 구도 스케치 이미지, 스타일 이미지를 순서대로 입력한다.
이어서, 하단의 실행 버튼을 클릭하여 워크플로를 실행한다.
실행 순서대로 우측 이미지 프리뷰 노드를 통해 생성된 이미지를 확인할 수 있다.
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/14.png" />

