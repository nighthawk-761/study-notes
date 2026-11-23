# Disk Scheduling과 RAID

<details>
<summary><strong>목차</strong></summary>

- [I/O Management와 Disk Scheduling](#section-1)
- [Disk Scheduling Policy](#section-2)
  - [FIFO](#section-3)
  - [Shortest Service Time First](#section-4)
  - [SCAN](#section-5)
  - [C-SCAN](#section-6)
  - [N-Step SCAN](#section-7)
  - [FSCAN](#section-8)
  - [기타 Disk Scheduling Policy](#section-9)
- [RAID](#section-10)
  - [RAID 0(Non-Redundant, Stripe)](#section-11)
  - [RAID 1(Mirrored)](#section-12)
  - [RAID 2(Redundancy through Hamming Code)](#section-13)
  - [RAID 3(bit-interleaved parity)](#section-14)
  - [RAID 4(block-level parity)](#section-15)
  - [RAID 5(block-level distributed parity)](#section-16)
- [Disk Cache](#section-17)
  - [Least Recently Used](#section-18)
  - [Least Frequently Used](#section-19)
  - [Frequently-based Replacement](#section-20)
- [복습 질문](#section-21)

</details>


Disk Scheduling Policy, RAID 구성과 Disk Cache 교체 정책을 정리합니다.

> 관련 노트: [Interrupt와 I/O](interrupts-and-io.md)

<a id="section-1"></a>
## I/O Management와 Disk Scheduling

<a id="section-2"></a>
## Disk Scheduling Policy

| Policy | 다음 요청 선택 | 장점 | 단점 |
| --- | --- | --- | --- |
| FIFO | 도착 순서 | 단순하고 공정함 | Head 이동 거리가 커질 수 있음 |
| SSTF | 현재 Head에서 가장 가까운 요청 | 평균 탐색거리 감소 | 먼 요청 starvation 가능 |
| SCAN | 한 방향으로 처리 후 끝에서 반전 | 대기시간 편차가 작음 | 방금 지나온 위치는 오래 대기 |
| C-SCAN | 한 방향만 처리하고 끝에서 처음으로 복귀 | 위치별 대기시간이 비교적 균일 | 복귀 이동 자체는 요청을 처리하지 않음 |
| N-Step SCAN | 요청을 N개 묶음으로 나눠 SCAN | 부하가 높아도 현재 묶음이 무한히 늘지 않음 | N 선택에 따라 성능 변화 |
| FSCAN | 두 Queue를 번갈아 SCAN | 처리 중 새 요청이 경로를 바꾸지 않음 | Queue 관리가 추가됨 |

```text
SCAN   : 0 <--- 요청 --- [HEAD] --- 요청 ---> MAX, 끝에서 방향 반전
C-SCAN : 0 <--- 요청 --- [HEAD] --- 요청 ---> MAX, 0으로 복귀 후 같은 방향 재개
```

<a id="section-3"></a>
### FIFO

<a id="section-4"></a>
### Shortest Service Time First

- 가장 optimal한 방식이다.
- 다만 starvation 가능성이 너무 높다.

<a id="section-5"></a>
### SCAN

- starvation 가능성은 거의 없다.

<a id="section-6"></a>
### C-SCAN

<a id="section-7"></a>
### N-Step SCAN

- Queue를 한꺼번에 처리하는 것이 아니라, N개씩 나눠서 처리하는 방식이다.
- 예측 가능성이 높아지는 scan 기법이다.
- 단, N의 값에 따라 성능이 달라질 수 있다.
    - N = 1이라면 그냥 FIFO다.

<a id="section-8"></a>
### FSCAN

<a id="section-9"></a>
### 기타 Disk Scheduling Policy

- Priority Scheduling
- Last-in First-out(LIFO)

<a id="section-10"></a>
## RAID

- Redundant Array of Independent Disks

| Level | 데이터 배치 | 중복성 | 핵심 특징 |
| --- | --- | --- | --- |
| RAID 0 | Block striping | 없음 | 빠르지만 디스크 하나만 고장 나도 전체 데이터 손실 |
| RAID 1 | Mirroring | 복제본 | 읽기와 복구가 단순하지만 저장 효율이 낮음 |
| RAID 2 | Bit-level striping | Hamming code | 오류 정정을 위한 별도 디스크가 많이 필요함 |
| RAID 3 | Bit-level striping | 전용 parity disk | 작은 단위 병렬 전송에 초점 |
| RAID 4 | Block-level striping | 전용 parity disk | parity disk가 병목이 될 수 있음 |
| RAID 5 | Block-level striping | 분산 parity | parity 병목을 여러 디스크로 분산 |

```text
          Disk 0   Disk 1   Disk 2
RAID 0      A0       A1       A2
            B0       B1       B2

RAID 1      A       A(copy)   -
            B       B(copy)   -

RAID 5      A0       A1       P(A)
            B0       P(B)     B1
            P(C)     C0       C1
```

<a id="section-11"></a>
### RAID 0(Non-Redundant, Stripe)


- 디스크가 N개가 있으면 N배의 속도가 난다.

<a id="section-12"></a>
### RAID 1(Mirrored)


- N개의 데이터 디스크와 N개의 복구 디스크로 구성되어 있다.

<a id="section-13"></a>
### RAID 2(Redundancy through Hamming Code)




<a id="section-14"></a>
### RAID 3(bit-interleaved parity)


<a id="section-15"></a>
### RAID 4(block-level parity)


<a id="section-16"></a>
### RAID 5(block-level distributed parity)


<a id="section-17"></a>
## Disk Cache

| Policy | 제거 기준 | 잘 맞는 상황 | 약점 |
| --- | --- | --- | --- |
| LRU | 가장 오래 사용되지 않은 Block | 최근 접근이 다시 반복되는 workload | 접근 순서 추적 비용 |
| LFU | 사용 횟수가 가장 적은 Block | 인기 Block이 오래 유지되는 workload | 과거 인기 Block이 남을 수 있음 |
| Frequency-based | 빈도와 최근성을 함께 반영 | 단기·장기 locality가 섞인 workload | 구현과 tuning이 복잡함 |

<a id="section-18"></a>
### Least Recently Used

<a id="section-19"></a>
### Least Frequently Used

<a id="section-20"></a>
### Frequently-based Replacement


<a id="section-21"></a>
## 복습 질문
