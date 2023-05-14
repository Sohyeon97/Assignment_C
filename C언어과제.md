# C언어 과제 (60p-89p)

- Lab : 동전 던지기 과제 (60p)

```
# 동전을 100번 던져서 앞면이 나오는 횟수와 뒷면이 나오는 횟수를 출력하기
  * 동전의 앞면 : 53
  * 동전의 뒷면 : 47
```

```
#include <stdlib.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <time.h> /*시간을 기준으로 랜덤한 값을 생성하기 위한 헤더 파일*/

int coin_toss(void); /*coin_toss 함수 선언*/

int main(void) /*메인 함수 정의*/
{
  int toss; /*동전을 던지는 횟수를 저장하는 변수 toss 정의*/
  int heads = 0; /*동전의 앞면이 나온 횟수를 저장하는 변수 heads 정의*/
  int tails = 0; /*동전의 뒷면이 나온 횟수를 저장하는 변수 tails 정의*/
  srand ((unsigned)time(NULL)); /* srand 함수를 호출하여 랜덤 시드를 초기화, Time엔 음수가 없기 때문에 Unsigned 필수 */

  for (toss = 0; toss < 100; toss++) /*for문을 사용하여 동전을 100번 던진다고 가정*/
  {
    if (coin_toss() == 1) 
      heads++; /*위에서 언급했던 coin_toss 함수를 호출, 동전을 던져서 앞면이 나오면 heads를 증가시킨다. */

    else
      tails++; /*if-else 함수 : 뒷면이 나오면 tails를 증가시킨다*/
  }

  printf("동전의 앞면: %d\n", heads); /*동전의 앞면이 나온 횟수 출력*/
  printf("동전의 뒷면: %d\n", tails); /*동전의 뒷면이 나온 횟수 출력*/
  return 0; /*프로그램 초기화, 종료*/
}

int coin_toss( void ) /*다시 coin_toss 함수를 정의함*/
{
  int head = rand() % 2; /*랜덤(rand)함수를 사용하여 나누기 2를 한 다음, head 변수에 저장한다.*/
  return head; /*head 변수를 반환*/
}
```

![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/b2443171-1d5a-4fe5-9531-2d24c1a33995)
<br>ㄴ 결과

<hr>

- Lab : 자동차 게임 (p.63)

```
# 난수를 이용하여서 자동차 게임을 작성해보자.
  1) car 1 ******************************************
  2) car 2 *****************************************************
```

```
#include <stdlib.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <time.h> /*시간을 기준으로 랜덤한 값을 생성하기 위한 헤더 파일*/
#include <conio.h> /*콘솔 입출력 함수를 제공하는 헤더, getch() 함수를 사용하기 위한 헤더, replit에서 오류 발생하여 뺐음*/

void disp_car(int car_number, int distance) /*차 번호와 이동한 거리를 입력받기 위한 함수*/
{
  int i; /*변수 i선언*/
  printf("CAR #%d:", car_number); /* Car번호 출력 */
  for(i=0; i < distance/10; i++) /*각 10km 단위마다 '*'을 출력하는 for문*/
  {
    printf("*"); /*차량 번호와 함께 '*'의 개수를 출력*/
  }
  printf("\n"); /*줄 바꿈*/
}

int main(void) /*메인 함수 정의*/
{  
  int i; /*변수 i 선언*/
  int car1_dist=0, car2_dist=0; /*car1, car2의 거리 0으로 초기화*/

  srand((unsigned)time(NULL)); /*무작위(랜덤) 시드 설정, 난수를 발생시키기 위해 초기화, srand 함수를 호출하여 랜덤 시드를 초기화, Time엔 음수가 없기 때문에 Unsigned 필수 */

  for(i=0; i<6; i++) /*6번의 레이싱 진행을 위한 for문*/
    {
      car1_dist += rand() % 100; /* 0~99 사이의 랜덤한 숫자를 발생시켜 car1_dist에 누적*/
      car2_dist += rand() % 100; /* 0~99 사이의 랜덤한 숫자를 발생시켜 car2_dist에 누적*/
      disp_car(1, car1_dist); /*car1의 현재 거리 출력*/
      disp_car(2, car2_dist); /*car2의 현재 거리 출력*/
      printf("--------------------\n"); /*구분선*/
      _getch(); /*본래는 한 번에 하나씩 출력하기 위한 사용자의 입력 대기, 하지만 replit에서 오류 발생하여 뺐음 */
    }
  return 0; 
}
```
![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/f26bee39-2364-40b3-a569-b88d2fdf8b3b)
<br>ㄴ#include <conio.h>, _getcha() 오류 발생
<br>
<br>![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/f8f32b16-7a11-4843-a320-1226fdce57b5)
<Br> ㄴ 결과 

<hr>
