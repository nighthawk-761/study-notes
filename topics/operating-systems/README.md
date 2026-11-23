# 3-1 운영체제

강의 순서가 아닌 **운영체제 개념의 학습 흐름**에 따라 재구성한 정리 노트입니다.

> 공개용 노트에서는 과제 자료와 제3자 교안 이미지를 제외했습니다. 상태 전이와 구조 설명은 직접 작성한 Mermaid 도식으로 제공합니다.

## 1. 운영체제 기초

- [Operating System 개요](operating-system-overview.md) — 운영체제의 역할, 자원 관리, 발전 과정과 Architecture
- [Interrupt와 I/O](interrupts-and-io.md) — Interrupt 종류, 처리 과정과 I/O 상태 변화
- [Memory Hierarchy](memory-hierarchy.md) — Cache, Main Memory와 저장장치 사이의 데이터 이동

## 2. Process와 Thread

- [Process와 Process State](processes.md) — Process 생성, 상태 변화, PCB와 Process Image
- [Context Switching](context-switching.md) — Context, Process, Mode Switch의 차이와 전환 과정
- [Thread와 Multithreading](threads.md) — Thread 모델과 운영체제별 구현 방식

## 3. 동시성과 동기화

- [Concurrency와 Mutual Exclusion](concurrency-and-mutual-exclusion.md) — Race Condition과 상호배제 기법
- [Semaphore, Monitor와 동기화 문제](synchronization-primitives.md) — Semaphore, Monitor와 고전적 동기화 문제
- [Deadlock](deadlocks.md) — 발생 조건, Prevention, Avoidance, Detection과 복구

## 4. 메모리 관리

- [Memory Management](memory-management.md) — Partitioning, Paging, Segmentation과 주소 변환
- [Virtual Memory](virtual-memory.md) — Page Table, TLB, Replacement Policy와 운영체제별 구현

## 5. Scheduling

- [CPU Scheduling](cpu-scheduling.md) — FCFS, RR, SPN, SRT, HRRN과 Feedback Queue
- [Multiprocessor Scheduling](multiprocessor-scheduling.md) — Load Sharing, Gang, Dedicated, Dynamic Scheduling
- [Real-Time 및 운영체제별 Scheduling](real-time-and-system-scheduling.md) — Real-Time, Windows, UNIX, Linux Scheduling

## 6. 저장장치

- [Disk Scheduling과 RAID](disk-scheduling-and-raid.md) — Disk Scheduling Policy, RAID와 Disk Cache

## 외부 참고 자료

- [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/) — Process, Scheduling, Concurrency, Virtual Memory를 무료 장별 문서로 복습
- [Linux Kernel Documentation](https://docs.kernel.org/) — Linux의 Scheduling, Memory Management, Driver 구현 참고
- [Windows Internals](https://learn.microsoft.com/en-us/sysinternals/resources/windows-internals) — Windows Process, Thread, Memory, I/O 구조 안내
- [Intel 64 and IA-32 Manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html) — Interrupt, Protection, Paging의 하드웨어 동작 참고
