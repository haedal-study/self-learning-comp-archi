# 7장

## 7-1. 다양한 보조기억장치

> _보조기억장치엔 다양한 종류가 있으나, 대중적으론 하드 디스크, 플래시 메모리가 있다._

### 하드 디스크

> _자기적인 방식으로 데이터를 저장하는 보조기억장치_

#### **구성 요소**

<img src="https://t1.daumcdn.net/cfile/tistory/99A3C44B5B3B06DD04" alt="disk" style="zoom:50%;" />

- Flatter
  - 실질적으로 데이터가 저장되는 원판
  - 자기 물질로 덮여 있어 수많은 N, S 극을 저장하며 각각은 0, 1 의 역할을 수행한다.
  - 하드 디스크는 일반적으로 여러 겹의 플래터로 이루어져 있으며, 플래터의 양면 모두 사용할 수 있다.
    이 때, 양면 플래터를 사용하면 위아래로 플래터당 두 개의 헤드가 사용된다.
- Spindle Motor
  - 플래터를 회전시키는 요소이다.
  - 스핀들이 플래터를 돌리는 속도는 분달 회전수를 나타내는 RPM(Revolution Per Minute)이라는 단위로 표현한다.
    - RPM 15,000 인 하드 디스크는 1분에 15,000 바퀴를 회전하는 하드 디스크이다.
- Head
  - 플래터를 대상으로 데이터를 읽고 쓰는 요소이다.
  - 플래터 위에서 미세하게 떠 있는 채로 데이터를 읽고 쓰는 바늘같이 생긴 부품이다.
  - 원하는 위치로 헤드를 이동시키는 Disk Arm(a.k.a Actuator Arm) 에 부착되어 있다.
  - 헤드의 트랙별 개수에 따라 **단일 / 다중 헤드 디스크** 로 분류된다.
    - 다중 헤드 디스크 (multiple-head disk): 헤드가 트랙별로 여러 개 달려 있는 디스크. 트랙마다 헤드가 있으므로 탐색 시간이 들지 않는다.
  - 헤드의 움직임 여부에 따라 **고정 / 이동 헤드 디스크** 로 분류된다.

#### **플래터에 데이터가 저장되는 방식**

> _플래터는 트랙과 섹터라는 단위로 데이터를 저장한다._

![flatter](https://www.pctechguide.com/wp-content/uploads/2011/09/31format.jpg)

**구성 요소**

- Track
  - 플래터를 여러 동심원으로 나누었을 때, 그 중 하나의 원을 트랙이라고 부른다.
- Sector
  - 플래터가 여러 조각으로 나뉜 요소이며, 하드 디스크의 가장 작은 전송 단위이다.
  - 하나의 섹터는 일반적으로 512바이트 정도의 크기를 가지고 있으나, 이는 하드 디스크에 따라 차이가 있다.
- Cylinder
  - 여러 겹의 플래터 상에서 같은 트랙이 위치한 곳을 모아 연결한 논리적 단위이다.
  - 같은 트랙끼리 연결한 원통 모양의 공간이다.
  - 연속된 정보는 보통 하나의 Cylinder 에 기록된다. 이는 디스크 암을 움직이지 않고 데이터에 접근할 수 있어서이다.

#### **플래터에 저장된 데이터에 접근하는 방식**

![time](data:image/png;base64,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)

**하드 디스크가 저장된 데이터에 접근하는 시간**

- 탐색 시간(Seek Time): 접근하려는 데이터가 저장된 트랙까지 헤드를 이동시키는 시간
- 회전 지연(Rotational Latency): 헤드가 있는 곳으로 플래터를 회전시키는 시간
- 전송 시간(Transmission Time): 하드 디스크와 컴퓨터 간에 데이터를 전송하는 시간

​

### 플래시 메모리

> _전기적으로 데이터를 읽고 쓸 수 있는 반도체 기반의 저장 장치_ > _플래시 메모리는 비단 보조기억장치의 범주 뿐만이 아닌, 다양한 곳에서 널리 사용되는 저장 장치이다._ > _가령, ROM 이나 우리가 접하는 대부분의 전자 제품에 플래시 메모리가 내장되어 있다._

#### **플래시 메모리 종류**

> _하나의 셀에 몇 비트를 저장할 수 있느냐에 따라 플래시 메모리 종류가 나뉜다._

<img src="https://blog.kakaocdn.net/dn/bHeLPB/btruZQUMfQ2/lQAmVRfJOb2hHwkCkyZaO0/img.png" alt="slc,mlc" style="zoom:48%;" />

**SLC**

- SLC 타입은 가장 빠른 비트의 입출력이 가능하다.
- 수명도 가장 길어 수만, 수십만 번 가까이 데이터를 지우고 쓸 수 있다.
- 그러나 가격이 가장 높다. 고성능의 빠른 저장 장치가 필요한 경우 사용한다.

**MLC**

- MLC 타입은 SLC 타입보다 대용화하기 유리하다.
- 시중에서 사용되는 많은 플래시 메모리 저장 장치들이 MLC 나 TLC 로 만들어진다.

**TLC**

- 한 셀당 3비트씩 저장할 수 있다. 즉, 8개의 정보를 표현할 수 있다.

#### **플래시 메모리 구성 요소**

![blocks, page](https://flashdba.files.wordpress.com/2014/06/nand-flash-die-layout.png)

- Page
  - 셀 들이 모여 만들어진 단위이다.
  - 플래시 메모리에서 **읽기 / 쓰기** 는 페이지 단위로 이주어진다.
  - 페이지는 세 개의 상태를 가질 수 있다.
    - Free: 어떤 데이터도 저장하고 있지 않아 새로운 데이터를 저장할 수 있는 상태
    - Valid
      - 이미 유효한 데이터를 저장하고 있는 상태.
      - 플래시 메모리는 덮어 쓰기가 불가능하므로, Valid 상태인 페이지는 새 데이터를 저장할 수 없다.
    - Invalid
      - 쓰레기값이라 부르는 유효하지 않은 데이터를 저장하고 있는 상태
      - Valid 상태인 페이지에 수정이 필요할 때 덮어쓰기가 불가능하므로,
        기존 페이지를 Invalid 상태로 만들고 Free 상태인 페이지에 새로운 데이터를 저장한다.
- Block:
  - 페이지가 모여 만들어진 단위이다.
  - 플래시 메모리에서 **삭제** 는 블록 단위로 이루어진다.
    - Invalid 상태인 페이지는 용량 낭비이므로 이를 제거해야 하는데, 플래시 메모리의 삭제는 Block 단위이므로 페이지에 있던 정보들이 날아간다.
      최근 SSD 를 비롯한 플래시 메모리는 **Garbage Collection** 기능을 제공해서,
      Valid 상태인 페이지를 새로운 블록으로 복사한 후 기존 블록을 삭제한다.
- Plane: 블록이 모여 만들어진 단위이다.
- Die: 플레인이 모여 만들어진 단위이다.

## 7-2. RAID의 정의와 종류

> _1TB 하드 디스크 4개로 RAID 를 구성하면 4TB 하드 디스크 한 개의 성능과 안전성을 능가할 수 있다._

### RAID 의 정의

- RAID(Redundant Array of Independent Disks) 는 주로 하드 디스크와 SSD 를 사용하는 기술이며,
  데이터의 안정성 혹은 높은 성능을 위해 여러 개의 물리적 보조장치를 하나의 논리적 보조기억장치처럼 사용하는 기술이다.

### RAID 의 종류

RAID 를 구성하는 방법은 여러 가지가 있다. 이 구성 방법을 **RAID 레벨** 이라고 표현한다.

#### RAID 레벨

![raid level](https://i0.wp.com/ipwithease.com/wp-content/uploads/2016/10/what-is-raid-dp.jpg)

**RAID 0 (Striping)**

- 데이터를 저장할 때 여러 개의 보조장치에 번갈아 저장한다.
  - 이 때, 줄무늬처럼 분산해서 저장된 데이터를 **stripe** 이라 하며, 분산하여 저장하는 것을 **striping** 이라고 한다.
- 데이터를 동시에 읽을 수 있기 때문에 하나의 디스크를 사용하는 것에 비해 속도가 빠르다.
- 그러나, 저장된 정보가 안전하지 않다는 단점이 있다.
  - 하나의 하드 디스크에 문제가 생기면 다른 모든 디스크 정보를 읽는 데 문제가 생길 수 있기 때문이다.

**RAID 1 (Mirroring)**

- 어떠한 데이터를 쓸 때 원본과 복사본 두 군데에 쓴다.
  - 안정성은 높아지나, 읽기 / 쓰기 속도가 RAID 0 에 비해 느리다.
- 저장 용량이 적어지므로 더 많은 양의 하드 디스크가 필요하게 되고, 비용이 증가한다.

**RAID 4 (Parity Bit)**

- RAID 1 처럼 완벽한 복사본을 만드는 대신, 오류를 검출하고 복구하기 위한 정보를 저장한 장치를 둔다.
  - 즉, `Parity Bit` 를 저장한다.
  - 원래 패리티 비트는 오류 검출만 가능할 뿐 복구는 불가능하다.
  - 그러나, RAID 에서는 검출 뿐만 아니라 복구도 가능하다.
  - 해당 장치를 이용해 다른 장치들의 오류를 검출하고, 오류가 있다면 복구한다.
- RAID 1 에 비해 적은 하드 디스크로도 데이터를 안전하게 보관할 수 있다.
- 그러나 어떤 새로운 데이터가 저장될 대마다 패리티를 저장하는 디스크에도 데이터를 쓰게 되므로,
  패리티 저장 장치에 병목 현상이 발생한다.

**RAID 5**

- RAID 4 에서의 병목 현상을 해결하기 위해, 각각의 하드 디스크에 패리티를 분산하여 저장한다.

**RAID 6**

- 기본적으론 RAID 5 와 같으나 서로 다른 두 개의 패리티를 둔다. 즉, 오류를 검출하고 복구할 수 있는 수단이 두 개가 주어진다.
- 그러나 새로운 정보를 저장할 때마다 패리티를 두 개 저장해야 하므로 쓰기 속도가 RAID 5 에 비해 느리다.
