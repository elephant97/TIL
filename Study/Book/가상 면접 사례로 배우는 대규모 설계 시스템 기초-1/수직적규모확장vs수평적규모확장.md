# 스케일 업(Scale up) 수직적 규모 확장 프로세스

<aside>
💡 서버에 고사양 자원( 더 좋은 CPU, 더 많은 RAM등)을 추가하는 행위를 말함

</aside>

- **👉🏻 장점**
    - 구현의 단순성
        - 하드웨어를 강화하는 것만으로 성능 향상이 가능하여, 시스템 구성 변경이나 추가적인 관리 작업이 적음
    - 관리 용이성
        - 서버의 수가 적어 관리가 비교적으로 간단함
- **👉🏻 단점**
    - 스케일 업의 한계
        - 하드웨어의 성능 업그레이드에는 물리적 한계가 있으며, 특정 지점 이상에서는 추가적인 성능 향상이 어려움
    - 비용 증가
        - 고성능 서버는 비용이 많이 들며, 업그레이드 비용도 상대적으로 높음
    - 가용성 문제
        - 단일 서버에 의존하는 구조는 해당 서버에 문제가 발생했을 때 전체 시스템의 가용성에 영향을 줄 수 있음
- **👉🏻 어느 상황에 유리할까?**
    - 데이터가 중앙 집중식 관리가 필요한 작거나 중간 규모의 애플리케이션
    - 애플리케이션의 복잡성을 최소화하고 싶을 때
    - 관리해야하는 서버의 수를 최소화 하고 싶을 떄

### 스케일 아웃(Scale out) 수평적 규모 확장 프로세스

<aside>
💡 더 많은 서버를 추가하여 성능을 개선하는 행위를 말함

</aside>

- **👉🏻 장점**
    - 확장성
        - 추가적인 서버를 계속해서 추가함으로써 거의 무한에 가까운 확장이 가능함
    - 유연성
        - 수요에 따라 서버를 추가하거나 제거할 수 있어, 비용 효율적인 운영이 가능함
    - 고가용성
        - 다수의 서버로 구성되어 있어, 단일 지점의 장애가 전체 시스템에 미치는 영향을 줄일 수 있음
- **👉🏻 단점**
    - 복잡성 증가
        - 여러 서버를 관리해야 하며, 데이터 일관성 유지, 네트워크 구성, 부하 분산 등 추가적인 관리 작업이 필요함
    - 초기 설정 비용
        - 부하 분산기, 네트워크 구성 등 초기 시스템 설정에 더 많은 작업과 비용이 발생할 수 있음
    - 데이터 관리
        - 데이터가 여러 서버에 분산되어 있을 때 일관성과 무결성을 유지하기 위한 추가적인 메커니즘이 필요함
        - ✅ 어떤 추가적인 메커니즘이 있을까?
            
            <aside>
            💡 여러 서버에 걸처 데이터를 분산하여 관리할 때 일관성, 무결성, 가용성을 유지하기 위해 
            다양한 메커니즘과 기술이 사용된다.
            이러한 메커니즘은 분산 시스템의 복잡성을 관리하고, 데이터를 효율적으로 동기화하며, 
            시스템 장애에 대응하는데 중요하다.
            
            </aside>
            
            - 데이터 복제(Replication)
                - 데이터 복제는 데이터를 여러 노드(서버)에 복사하여 보관하는 프로세스
                - 하나의 노드에 장애가 발생해도 다른 노드에서 데이터를 가져올 수 있어 시스템의 가용성과 내구성이 향상됨
                - 데이터 복제는 주로 읽기 성능을 향상시키고 데이터의 가용성을 높이는데 사용됨
                
            - 샤딩(Sharding)
                - 대규모의 데이터 셋을 작은 파편(샤드)으로 분할하여 여러 서버에 분산 저장하는 방식
                - 각 샤드는 독립적으로 데이터를 저장하고 처리할 수 있고, 이를 통해 데이터베이스의 
                쓰기 및 읽기 성능을 향상시킬 수 있다.
                - 샤딩은 데이터의 복잡성을 증가시키지만, 확장성과 성능 최적화에 유리함
                
            - 일관성 모델(Consistency Models)
                - 분산 시스템에서는 강한 일관성, 최종 일관성, 인과 일관성 등 다양한 일관성 모델을 적용할 수 있다.
                - 각 모델은 데이터 일관성 유지 방식과 성능, 가용성 사이의 균형을 다르게 설정함
                - 시스템의 요구 사항에 따라 적절한 일관성 모델을 선택하여 데이터의 일관성을 관리함
                
            - 트랜잭션 관리(Transaction Management)
                - 분산 데이터베이스 시스템에서는 분산 트랜잭션을 관리하기 위해 2단계 커밋
                (2-phase commit) 프로토콜이나 3단계 커밋(3-phase commit) 프로토콜 같은 알고리즘을 사용
                - 이러한 프로토콜은 모든 노트에서 트랜잭션이 일관되게 커밋되거나 롤백되도록 보장
                - ✅ 2단계 커밋, 3단계 커밋 프로토콜이란?
                    - 2단계 커밋 프로토콜
                        - 2PC는 트랜잭션의 커밋 과정을 두 단계로 나누어 진행한다
                        1. 준비단계
                            - 트랜잭션 관리자가 모든 참여 노드에게 트랜잭션 커밋 준비를 지시하고, 각 노드는 작업을 완료할 수 있는지를 확인한 후 준비 완료 여부를 관리자에게 응답함
                        2. 커밋단계
                            - 모든 참여 노드로부터 준비 완료 응답을 받으면 관리자는 모든 노드에게 커밋을 지시함
                            - 만약 어떤 노드라도 준비 실패 응답을 보낸경우, 관리자는 모든 노드에게 트랜잭션을 롤백하라는 지시를 보냄
                            
                    - 3단계 커밋 프로토콜
                        - 3PC는 2PC의 단점을 일부 해결하기 위해, 추가적인 단계를 도입한 프로토콜
                        - 트랜잭션 처리 과정에서 발생할 수 있는 네트워크 파티션(분할)이나 단일 실패 지점의 영향을 줄이고자 함
                        - 3PC는 다음 3단계로 구성됨
                        1. 준비단계
                            - 트랜잭션 관리자가 모든 참여 노드에게 트랜잭션 커밋 준비를 요청함
                        2. 미리 커밋 단계
                            - 모든 노드가 준비 완료 응답을 보내면, 관리자는 모든 노드에게 미리 커밋(pre-commit) 상태임을  알림
                            - 이 단계에서 아직 커밋을 완료하지 않으며, 모든 노드가 커밋 준비가 되었음을 확인하는 과정임
                        3. 커밋 단계
                            - 모든 노드가 미리 커밋 상태에 동의하면, 관리자는 최종적으로 커밋을 진행하라는 지시를 함
                            - 만일 pre-commit 단계에서 문제가 발생하면, 롤백이 수행됨
                    
                    - 비교 및 특징
                        - 2단계 커밋 프로토콜
                            - 구현이 간단하고 널리 사용되지만, 준비 단계에서 어떤 노드가 실패하면 시스템이 블록될 수 있는 단점이 있음
                            - 하나 실패시 전체의 실패로 이어질 수 있음
                        - 3단계 커밋 프로토콜
                            - 추가적인 단계를 통해 시스템의 내결함성을 높이고, 단일 실패 지점에 대한 
                            의존도를 줄임
                            - 하지만 추가적인 네트워크 트래픽과 복잡성을 초래할 수 있으며, 극단적인 상황에서는 여전히 실패 가능성이 존재함
                            
            - 부하 분산(Load Balancing)
                - 부하 분산은 클라이언트의 요청을 여러 서버에 고르게 분배하는 기술
                - 이를 통해 단일 서버에 집중되는 부하를 줄이고, 전체 시스템의 처리량과 가용성을 향상시킴
                - 부하 분산기는 동적으로 트래픽을 관리하고, 서버의 상태를 모니터링하여 효율적으로 요청을 분배함
                
            - 장애 감지 및 복구(Failure Detection and Recovery)
                - 분산 시스테에서는 서버 또는 네트워크의 장애를 신속하게 감지하고 자동으로 복구할 수 있는 매커니즘이 필수적임
                - 이를 위해 하트비트 매커니즘, 재시도 로직, 데이터 복구 프로토콜 등을 사용하여 시스템 내구성을 강화시킴
                - ✅ 하트비트 매커니즘이란?
                    
                    <aside>
                    💡 분산 시스템이나 네트워크에서 각 구성 요소(노드, 서버)의 상태를 모니터링 하기 위해 사용되는 기술
                    
                    이 매커니즘의 핵시은 정기적으로 “생명 신호” 또는 “하트비트 신호”를 전송하여, 시스템의 다른 부분들이 해당 구성 요소가 여전히 작동 중이고 접근 가능한 상태에 있음을 확인하는 것
                    
                    </aside>
                    
                    - **작동 방식**
                        - 신호 전송
                            - 시스템 내의 노드(또는 서버)는 정해진 시간 간격으로 하트비트 신호를 다른 
                            노드나 관리 서버에 보냄
                        - 상태 확인
                            - 신호를 받는 노드(또는 관리 시스템)은 이 신호를 통해 전송한 노드의 상태가 정상적임을 확인 함
                        - 타임아웃과 장애 감지
                            - 만약 정해진 시간 내에 하트비트 신호를 받지 못한다면, 신호를 기다리는 노드
                            (또는 관리시스템)은 해당 노드가 실패했거나 네트워크에 문제가 발생했을 가능성이 있다고 판단
                        - 대응 조치
                            - 장애가 감지되면, 시스템은 사전 정의된 대응 조치를 취함
                            - 장애 복구 절차를 시작하거나, 관리자에게 경고를 보내는 것 등이 될 수 있음
                    - **장점**
                        - 실시간 모니터링
                            - 시스템의 구성 요소가 정상 작동하는지 실시간으로 모니터링 할 수 있어, 문제를 신속하게 탐지하고 대응할 수 있음
                        - 자동화된 장애 대응
                            - 하트비트 매커니즘을 통해 문제가 발생한 구성 요소를 자동으로 식별하고 필요한 경우 자동 복구 절차를 실행할 수 있음
                        - 높은 가용성
                            - 시스템의 구성 요소 간에 지속적으로 상태 정보를 교환함으로써, 전체 시스템의 가용성을 높일 수 있음
- **👉🏻 어느 상황에 유리할까?**
    - 대규모 데이터 처리가 필요한 애플리케이션
    - 높은 가용성과 장애 허용이 중요한 시스템
    - 사용량이 시간에 따라 크게 변하는 웹 애플리케이션
