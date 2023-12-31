# 검투사 키우기
<img src="https://github.com/DWBoo/Gladiator/assets/147593910/59861653-d37a-4ece-a316-282072ac8d91" width="40%" height="30%">
<img src="https://github.com/DWBoo/Gladiator/assets/147593910/08a1981c-47dc-4934-82e1-e6769c999f9c" width="40%" height="30%">
<img src="https://github.com/DWBoo/Gladiator/assets/147593910/07b1ba63-65d3-450a-8b94-44f8e9859802" width="40%" height="30%">
<img src="https://github.com/DWBoo/Gladiator/assets/147593910/2d6483d1-da51-438d-8060-772196a7339e" width="40%" height="30%">
<img src="https://github.com/DWBoo/Gladiator/assets/147593910/ce452403-c1a8-40a6-a6a1-4237242eec27" width="40%" height="30%">

검투사를 성장시키고 유저와 결투를 하는 횡 스크롤 방치형 게임

# 작업 부분
실시간 채팅, 대결 및 상점 등 서버가 필요한 부분은 직접 서버를 구현한 것이 아닌 모두 "뒤끝"이라는 이미 서버 기능이 구현되어 제공되는 서비스를 이용했다. 이렇게 전달받은 데이터를 이용하여 클라이언트만 구현

# 어려웠던 점
해당 서비스는 실시간 채팅, 대결을 제외하고는 실시간 서버와 달리 서버에서 처리한 후 결과만을 전달해 주는 것이 아니기에 데이터를 받아와서 직접 클라이언트에서 구현을 해줘야 했다. 즉, 서버에 구현을 하는 것이 아닐 뿐 서버와 비슷하게 데이터를 이용해서 아이템 구매, 업그레이드 등 기능을 구현해야 했다. 하지만 서버에 대한 지식이 전무한 상태라 아이템 구매의 구현을 골드량 읽기 -> 구매액보다 골드가 많으면 구매 성공 -> 골드 차감 -> 인벤토리에 아이템 추가 이런 식으로 단계별로 모두 구현을 해주고 있는데, 여기서 문제가 만약 이 단계 중 하나라도 실패한다면 구매 실패처리를 한 후 모두 다시 원래대로 되돌리는 데이터 업데이트 작업을 모두 일일 진행

# 해결책
서버에 대해 전무한 상태라도 느낌적으로 잘못 된 방향으로 가고 있다는 것이 느껴졌고 서버에 대해 검색을 좀 해보니 "트랜잭션"이라는 개념을 알게 되었고 서비스에 이와 관련하여 문의를 해보니 트랜잭션 기능을 제공해주고 있었다. 그래서 트랜잭션 기능을 이용하여 아이템 구매뿐 아니라 잘못 구현한 다른 기능들 까지 모두 바꿔야 했다.
