# ComfyUI on Amazon SageMaker AI Studio
이 저장소는 Amazon SageMaker AI Studio에서 ComfyUI를 설치하고 실행하는 방법을 안내합니다.

## 목차
1. [SageMaker AI Studio 환경 설정](#step-1-amazon-sagemaker-ai-studio-환경-설정)
2. [ComfyUI 설치 및 환경 설정](#step-2-주피터랩-스페이스에서-comfyui-설치-및-환경-설정)
3. [ComfyUI 기동 및 접속](#step-3-comfyui-기동-및-접속)
4. [ComfyUI 워크플로 불러오기 및 GUI 초기 설정](#step-4-comfyui-워크플로-불러오기-및-gui-초기-설정)
5. [ComfyUI 워크플로 실행하기](#step-5-comfyui-워크플로-실행하기)
6. [결과 이미지 확인](#step-6-결과-이미지-확인)
7. [워크플로 추가 설명](#step-7-워크플로-추가-설명)

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

## Step 6. 결과 이미지 확인
<table>
  <tr>
    <td>
      <img src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/ComfyUI_temp_fdtnx_00003_.png"" /><br/>
      원본 상품 이미지
    </td>
    <td>
      <img src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/ComfyUI_temp_jnkxy_00005_.png" /><br/>
      배경 생성 초안 이미지
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/ComfyUI_temp_ijgfb_00005_.png" /><br/>
      1차 보완 이미지
    </td>
    <td>
      <img src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img//ComfyUI_temp_geayj_00005_.png" /><br/>
      2차 보완 이미지
    </td>
  </tr>
</table>

2차 보완 이미지를 4배로 upscale한 이미지
<img width="4418" height="1998" alt="1" src="https://github.com/Hyunsoo0128/comfyui_on_SageMakerAI/blob/main/img/ComfyUI_temp_tdmpe_00005_.png" />

## Step 7. 워크플로 추가 설명
# 목적 : AI 기반 제품 이미지 자동 생성
해당 ComfyUI 워크플로는 3개의 입력 이미지(상품, 구도, 스타일)를 활용하여, 전문적인 느낌의 고해상도 제품 홍보 이미지를 생성하도록 설계되었습니다. 
복잡한 배경 생성과 합성을 자동화하여 작업 효율을 극대화합니다.

# 주요 기능
* 다중 컨트롤넷(Multi-ControlNet) 제어: 깊이(Depth)와 캐니(Canny) 맵을 동시에 사용하여 상품의 입체감과 전체적인 구도를 정교하게 제어합니다.
* IPAdapter를 통한 스타일 전이: 특정 실내 공간 이미지의 스타일(조명, 색감, 질감)을 생성될 배경에 완벽하게 적용합니다.
* 인페인팅(Inpainting)을 활용한 배경 생성: 상품 이미지를 제외한 배경 영역에만 새로운 이미지를 생성하여 자연스러운 합성을 구현합니다.
* 다단계 KSampler 리파인먼트: 여러 단계의 KSampler를 거치며 이미지의 디테일과 완성도를 점진적으로 향상시킵니다.
* 고해상도 업스케일링: 최종 결과물을 4배 업스케일링하여 상업적 용도로도 손색없는 고품질 이미지를 제공합니다.

# 워크플로우 상세 설명
이 워크플로우는 크게 입력 및 전처리, 1차 배경 생성, 2-3차 리파인먼트, 최종 업스케일링의 4단계로 구성됩니다.

1. 입력 및 전처리 (Inputs & Preprocessing)
1.1. 상품 이미지 (Product Image):
Image Rembg 노드를 통해 배경이 자동으로 제거됩니다.
DepthAnythingPreprocessor로 깊이 맵을 추출하여 상품의 3D 형태를 유지하는 데 사용됩니다.

1.2. 구도맵 이미지 (Composition Map):
XYZ 축이 스케치된 간단한 구도 이미지입니다.
CannyEdgePreprocessor를 통해 외곽선(Edge)을 추출하여 바닥, 벽 등 공간의 전체적인 구조를 제어하는 데 사용됩니다.

1.3. 스타일 이미지 (Style Image):
원하는 분위기의 실내 공간 사진입니다.
이 이미지는 IPAdapterAdvanced 노드에 직접 입력되어 생성될 배경의 스타일을 결정합니다.

2. 1차 배경 생성 (Pass 1: Background Generation via Inpainting)
2.1. 배경이 제거된 상품 이미지에서 마스크(Mask)를 생성하고, 이를 반전(Invert Mask)시켜 배경 영역만 선택합니다.
2.2. VAEEncodeForInpaint 노드는 이 마스크를 기반으로 배경 영역만 Latent 공간에서 비워둡니다.
2.3. ControlNet(Depth, Canny)과 IPAdapter(Style)의 조건이 모두 적용된 상태에서 KSampler가 비어있는 배경 영역을 채우며 이미지를 생성합니다.
이 단계의 결과물은 상품과 배경이 최초로 합쳐진 이미지입니다.

3. 2-3차 리파인먼트 (Pass 2 & 3: Refinement)
3.1. 추가 KSampler with IPAdapter:
생성된 초안 이미지를 다시 Latent로 변환한 후, 낮은 denoise 값(예: 0.4)으로 다시 샘플링합니다.
이 과정에서 IPAdapter와 ControlNet의 영향을 받으며 상품과 배경이 더욱 자연스럽게 어우러지고 스타일이 강화됩니다.
3.2. 추가 KSampler without IPAdapter:
1차 보완 결과물을 다시 Latent로 변환하고, 더 낮은 denoise 값(예: 0.2)으로 최종 샘플링을 진행합니다.
이 단계에서는 IPAdapter의 영향을 받지 않는 기본 모델을 사용하여 이미지의 전반적인 디테일을 정리하고 완성도를 높입니다.

4. 최종 업스케일링 (Final Upscaling)
모든 리파인먼트 과정이 끝난 이미지는 ImageUpscaleWithModel 노드로 전달됩니다.
4x-UltraSharp과 같은 업스케일링 모델을 사용하여 최종 결과물을 고해상도로 변환합니다.


