# FineGymVideo-Temporal-Action-Localization
Fine-Gym-Temproal-Action-Localization
학부연구생에서 진행하고 있는 프로젝트입니다.

### Temporal Action Localization 
* 영상에서 액션 구간을 추출한 후, 구간에 대한 클래스를 판정해내는 작업

### FineGym Dataset
* 실내 체육 경기 영상 데이터 셋으로 동영상의 크기가 30분에서 3시간의 길이로 매우 큰 동영상이며, 유튜브에서 추출한 데이터 셋입니다.
* 영상의 크기가 크며, 실내 체육 도마, 점프 등 굉장히 빠른 액션이 포함되어 있어 보다 분석에 제약에 어려움이 있는 데이터 셋입니다.
* 이때까지 FineGym Dataset을 이용하여 Temporal Action Localization 작업을 한 저장소가 없어, 데이터 추출 가공 모델 개선 등 모든 작업을 진행 중에 있습니다.
* 경기 영상은 방송 영상에 해당하며, 이는 리플레이, 관중, 시점 변환, 확대 축소 등 다양한 요소들이 있습니다.

### GOAL
* 영상의 길이가 크며, 액션의 포착이 어려운 영상에 대해 액션 구간 추출을 성공해내도록 합니다.
* 이때까지 시도하지 않았던, FineGym Dataset을 이용하여 액션 구간 추출을 성공합니다.
* 어려운 데이터 셋인만큼 보다 액션을 잘 잡아내기 위하여 음성, flow data를 추가하여 성능을 높이고자 합니다.

### Process
* 영상 전체를 pretrained된 I3D model을 이용하여 RGB 피쳐를 추출합니다.
* 추출된 피쳐를 sliding window기법을 통하여 여러 구간을 추출하고 구간이 액션에 해당하는지 판별하는 모델을 만들어 후보 구간을 추출하는 작업을 거칩니다.
* 추출한 후보 구간을 이용하여 Muse model(방송 특화 액션 구간 추출 모델)을 개선시켜 FineGym에서 사용할 수 있도록 만든 다음 정답 액션 구간을 추출한 후 클래스를 판별합니다. 
* 음성 피쳐와 flow 피쳐를 추가적으로 사용하며 성능을 개선시킵니다.
