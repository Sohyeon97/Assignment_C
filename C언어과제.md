# C언어 과제 (60p-89p)

<h3><b>● Lab : 동전 던지기 과제 (p.60)</b></h3>

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

<h3><b>● Lab : 자동차 게임 (p.63)</b></h3>

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
  return 0; /*0으로 */
}
```
![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/f26bee39-2364-40b3-a569-b88d2fdf8b3b)
<br>ㄴ#include <conio.h>, _getcha() 오류 발생
<br>
<br>![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/f8f32b16-7a11-4843-a320-1226fdce57b5)
<Br> ㄴ 결과 

<hr>

 <h3><b>● 도전문제 (p.67)</b></h3>

```
# 자동차를 3개로 늘려보자
```

```
#include <stdlib.h> /*랜덤함수를 사용하기 위한 헤더 파일*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <time.h> /*시간을 기준으로 랜덤한 값을 생성하기 위한 헤더 파일*/
#include <conio.h> /*getch() 함수를 사용하기 위한 헤더, replit에서 오류 발생하여 뺐음*/


void disp_car(int car_number, int distance) /*차 번호와 이동한 거리를 입력받기 위한 함수*/
{
  int i; /*변수 i선언*/
  printf("CAR #%d:", car_number);
  for(i=0; i < distance/10; i++){ //각 10km 단위마다 '*' 출력
    printf("*"); /*차량 번호와 함께 '*'의 개수를 출력*/
  }
  printf("\n"); /*줄바꿈*/
}

int main(void) /*main함수 호출*/
{  
  int i; /*변수 i선언*/
  int car1_dist=0, car2_dist=0, car3_dist=0; /*car1, car2, car3의 거리 0으로 초기화*/

  srand((unsigned)time(NULL));  /*무작위(랜덤) 시드 설정, 난수를 발생시키기 위해 초기화, srand 함수를 호출하여 랜덤 시드를 초기화, Time엔 음수가 없기 때문에 Unsigned 필수 */

  for(i=0; i<6; i++) /*6번의 레이싱 진행을 위한 for문*/
    {
      car1_dist += rand() % 100; /*0~99사이의 난수를 발생시켜서 car1_dist에 누적*/
      car2_dist += rand() % 100; /*0~99사이의 난수를 발생시켜서 car2_dist에 누적*/
      car3_dist += rand() % 100; /*0~99사이의 난수를 발생시켜서 car3_dist에 누적*/
      disp_car(1, car1_dist); /*car1의 현재 거리 출력*/
      disp_car(2, car2_dist); /*car2의 현재 거리 출력*/
      disp_car(3, car3_dist); /*car3의 현재 거리 출력*/
      printf("--------------------\n"); /*줄바꿈*/
      _getch(); /*본래는 한 번에 하나씩 출력하기 위한 사용자의 입력 대기, 하지만 replit에서 오류 발생하여 뺐음 */
    }
  return 0; /*0으로 초기화*/
}
```
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/bee6f5f3-7d2b-4c37-a77b-9ba38cbb8186)
<br> ㄴ 결과
 
<hr>

 <h3><b>● 표준 라이브러리 함수(수학 함수) (p.68)</b></h3>
1) 수치 계산을 하는 라이브러리 함수를 이용하면 복잡한 산술 연산 가능 <br>
2) 수학 함수들에 대한 원형은 헤더파일 amth.h에 있다. 수학함수는 일반적으로 double형의 매개 변수와 반환값을 가짐. <br>
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/a7a03f36-8d39-4f71-9625-abdda75d5019)
<br> ㄴ 수학 라이브러리 함수 
 
 <hr>
 
 <h3><b> ● floor()와 ceil() 함수 (p.70) </b></h3>
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/c836fb61-ef9d-4a67-bc84-a1f63c9225c7)
 <br>ㄴ예를 들어 2.31의 값을 가지면 floor은 정수 2에, ceiling은 정수 3의 값을 가진다.
 <br>
 1) floor() 함수 : 내림함수 <br>
 2) ceil() 함수 : 올림함수 <br>
 
 ```
double result, value = 1.6;

result = floor(value); /*floor 함수를 사용하여 value의 소수점 아래를 버림.*/
printf("%lf", result); /* 버림 연산을 한 결과를 출력*/

result = ceil(value); /*ceil 함수를 사용하여 value의 소수점 아래를 올림*/
printf("%lf", result); /*올림 연산을 한 결과인 결과를 출력*/
 ```
 
 <hr>
 
 <h3><b> ● fabs() (p.71) </b></h3>
 1. fabs()는 실수를 받아서 절대값을 반환한다.

 ```
 printf("12.0의 절대값은 %f\n", fabs(12.0));
 printf("-12.0의 절대값은 %f\n", fabs(-12.0));
 ```

 <hr>
 
 <h3><b> ● pow()와 sqrt() (p.72) </b></h3>
 
 ```
 printf("10의 3승은 %.0.f\n",pow(10.0,3.0));
 printf("16의 제곱근은 %.0.f\n",sqrt(64));
 ```
 
1) pow 함수가 하는 일 : 베이스(base)가 되는 숫자의 n 제곱을 구하기
<br>(base의 n승이라고도 표현하고, 기호로는 base^n 으로도 표현)
 
2) sqrt 함수가 하는 일 : 매개변수 x로 들어온 숫자에 루트를 씌워서 계산한 값을 반환.
<br>즉, 루트 x를 구해주는 함수 (제곱근을 구해주는 함수).
 <br>
 
 # 예제
 
 ```
10의 3승은 1000
16의 제곱근은 4.
 ```

 ```
 // 삼각함수 라이브러리
#include <math.h> /*여러 수학 함수들을 포함하는 표준 라이브러리*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/

int main(void) /* main 함수 호출 */
{
    double pi = 3.141592635; /* pi값 지정 */
    double x, y; /* x, y 변수 지정*/

    x = pi / 2; /*x에 pi/2 값을 대입*/
    y = sin(x); /* x의 사인 값을 계산하여 y에 저장*/
    printf("sin(%f) = %f\n", x, y); // x와 y의 값을 출력합니다.

    y = cos(x); /*x의 코사인 값을 계산하여 y에 저장*/
    printf("cos(%f) = %f\n", x, y); /*x와 y의 값을 출력*/

    return 0; /*0으로 초기화 (교안에 없어서 추가)*/
}
```

![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/c56ced82-eab0-4996-b563-bd18e63f7170)
<br>ㄴ결과
 
 <hr>
 
 <h3><b> ● 중간 점검 (p.74) </b></h3>
 <h4> 1) 90도에서의 싸인값을 계산하는 문장을 작성하여 보아라.</h4>
 <br>ㄴ sin(90.0*(3.141592/180.0));
 <br>
 <h4> 2) rand() % 10 이 계산하는 값의 범위는? </h4>
 <br>ㄴ 0에서 9
 
 <hr>
 
 <h3><b> ● 기타 함수 (p.75) </b></h3>
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/3b7cf779-aa97-48c7-8219-41125b47f4dd)

```
#include <stdlib.h> /*랜덤함수를 사용하기 위한 헤더 파일*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/

int main(void) /*메인 함수 호출*/
{
    system("dir"); /* 현재 디렉토리의 파일 및 폴더 목록을 출력, "dir"은 윈도우에서 사용되는 명령어.*/
    printf("아무 키나 치세요\n"); /*사용자가 아무 키나 입력하게 하기 위해 안내 메시지를 출력.*/
    _getch(); /*사용자가 키를 입력. _getch() 함수는 윈도우환경에서 단일 키 입력을 처리*/
    system("cls"); /*화면을 지우고 콘솔 창을 깨끗하게 초기화. "cls"는 윈도우에서 사용되는 명령어*/

    return 0; /*0으로 초기화, 프로그램 종료*/
}
```
 <hr>
 
 <h3><b> ● Lab : 시간 맞추기 게임 (p.77) </b></h3>
 
 # 사용자에게 정확한 시간을 예측하게 하는 게임을 만들어보자. 
<br>사용자에게 10초가 지나면 엔터키를 누르라고 한 후에, 정확한 시간과 얼마나 차이나는지 출력

 ```
 10초가 되면 엔터키를 누르세요
 종료되었습니다.
 경과된 시간은 6초입니다.
 ```
 
 ```
#include <stdio.h>
#include <time.h>

int main(void)
{
    time_t start, end; /*time_t는 unsigned long과 동일하다*/
    start = time(NULL); /*현재 시간을 start에 저장*/

    printf("10초가 되면 아무 키나 누르세요\n"); /*사용자에게 10초가 되면 아무 키나 누를 것을 안내*/

    while (1)
    {
        if (getchar()) /* 만약 사용자가 키를 입력하면 루프를 빠져나옴 */
            break;
    }

    printf("종료되었습니다.\n"); /* 종료되었음을 안내 */

    end = time(NULL); /*현재 시간을 end에 기록, 저장*/
    printf("경과된 시간은 %ld 초입니다. \n", end - start); /*경과된 시간을 저장 및 출력*/.

    return 0; /*0으로 초기화, 프로그램 종료*/
}
```

 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/8c10aa39-5e65-43dd-98cf-2324f2ea08d2)
<Br>ㄴ 결과
 
 <hr>
 
 <h3><b> ● Lab : 나무 높이 측정 (p.79) </b></h3>
 
 # 각도기와 삼각 함수를 이용하면 나무의 높이를 측정할 수 있다.
 <br>다음 그림을 참조하여서 나무의 높이를 측정하는 프로그램을 작성하여보자.
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/117555db-cb8e-45d9-8fe3-80de1f6cacb6)

 ```
 나무와의 길이(단위는 미터) : 4.2
 측정자의 키(단위는 미터): 1.8
 각도(단위는 도): 62
 나무의 높이(단위는 미터): 9.699047
 ```
 
 ```
#include <math.h> /*여러 수학 함수들을 포함하는 표준 라이브러리*/
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/

int main(void) /*메인 함수 호출*/
{
    double height, distance, tree_height_degrees, radians; /*나무의 높이, 측정자의 키, 각도, 나무의 높이 변수 호출*/

    printf("나무와의 거리(단위는 미터): ");
    scanf("%lf", &distance); /*이용자가 나무의 거리를 입력하게 함*/

    printf("측정자의 키(단위는 미터): ");
    scanf("%lf", &height); /*사용자가 측정자의 키를 입력하게 함*/

    printf("각도(단위는 도): ");
    scanf("%lf", &tree_height_degrees); /*이용자가 나무의 각도를 입력*/

    radians = tree_height_degrees * (3.141592 / 180.0); /*입력된 각도를 라디안으로 변환*/

    double tree_height = tan(radians) * distance + height; /*나무의 높이를 계산*/
    printf("나무의 높이(단위는 미터): %lf\n", tree_height); /*계산된 나무의 높이를 출력*/

    return 0;/*프로그램 종료 및 0으로 초기화*/
}
```

<hr>
 
 <h3><b> ● Lab : 삼각함수 그리기 (p.81) </b></h3>
 
 # 우리는 삼각함수를 계산하는 라이브러리 함수를 학습하였다.
 <br>이것을 이용하여서 싸인함수 그래프를 90도 회전하여서 그려보자
 
 ![image](https://github.com/Sohyeon97/Assignment_C/assets/128660870/027f6df6-73c9-495a-89d1-8e3bd3bcf391)
 <br> ㄴ 출력 예시
 
 ```
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <math.h> /*여러 수학 함수들을 포함하는 표준 라이브러리*/

#define PI 3.141592 /*PI는 전처리기 지시문(preprocessor directive)으로 수학적으로 원주율(Pi)를 나타내며, 3.141592로 대락 표현*/

double rad(double degree) /*각도를 라디안으로 변환하는 함수*/
{
    return PI * degree / 180.0; /*주어진 degree 값을 라디안으로 변환하여 반환*/
}


void drawbar(int height) /*막대 그래프를 그리는 함수*/
{
    for (int i = 0; i < height; i++)
        printf("*"); /*만약 i라는 변수가 height 보다 작을 경우 i는 계속 증가하고(증감함수), "*"을 출력한다*/
    printf("\n"); /*줄바꿈*/
}

int main(void) /*main 함수 호출 */
{
    int degree, x, y; /* 3개의 변수 degree(각도 저장 변수), x, y(막대 그래프 높이 저장 변수) 선언 */
    
    for (degree = 0; degree <= 90; degree += 10) {
       /*각도 degree가 90도 보다 작거나 같을 경우, 10도씩 증가*/
       /*이때 sin 값은 -1.0~1.0이므로 정수로 반올림 하여 증폭*/
 
        y = (int)(60 * sin(rad((double)degree)) + 0.5); /*증폭된 값을 변수 y에 저장*/
        drawbar(y); /*drawbar() 함수를 호출하여 y 값을 매개변수로 전달하여 막대 그래프를 그림*/
    }
    
    return 0; /*0으로 초기화 및 프로그램 정상 종료*/
}
```
 
 <hr>
 
 <h3><b> ● 함수를 사용하는 이유 (p.83) </b></h3>
 
 1) 코드의 중복성을 없애준다.
 2) 제작된 함수는 다른 프로그램을 제작할 때도 재사용이 가능하다.
 3) 한 문제를 단순한 부분으로 분해할 수 있다.
 
 <hr>
 
 <h3><b> ● 복잡한 프로그램은 함수로 분리한다 (p.84) </b></h3>
 
 ```
 int main(void)
 {
   // 숫자들의 리스트를 키보드에서 읽어들이는 코드
   .....
   // 숫자들을 크기순응로 정렬하는 코드
   .....
   // 정렬된 숫자들의 리스트를 화면에 출력하는 코드
   .....
 ```
 ↓
 ```
 int main(void)
 {
   ...
   read_list(); // 숫자들의 리스트를 키보드에서 읽어 들이는 함수
   sort_list(); // 숫자들의 리스트를 크기 순으로 정렬하는 함수
   print_list(); // 숫자들의 리스트를 화면에 출력하는 함수
   ...
 }
 ```
 ㄴ 이처럼 함수를 사용하면 복잡한 프로그램을 보다 단순하게 표현할 수 있다.
 
 <hr>
 
 <h3><b> ● Mini Project : 공학용 계산기 프로그램 작성 (p.85-89) </b></h3>
 
 * 이번 장에서 학습한 함수들을 이용하여 사인값이나 코사인값을 계산할 수 있는
 <br>공학용 계산기를 만들어보자. 아직 구현 안 된 기능은 도전문제에서 추가해보자.
 
 ```
 1. 팩토리얼
 2. 사인
 3. 로그 (base 10)
 4. 제곱근
 5. 순열(nPr)
 6. 조합(nCr)
 7. 종료
 선택해주세요 : 1
 정수를 입력하시오 : 10
 결과 = 3628800
 ```
 
 ```
#include <stdio.h> /*C언어에서 랜덤함수를 사용하기 위한 헤더 파일*/
#include <math.h> /*여러 수학 함수들을 포함하는 표준 라이브러리*/


int menu(void) /*메뉴 출력과 선택을 위한 함수 호출*/
{
    int n; /*변수 n선언 (메뉴 선택을 위해 변수 n선언) */
    printf("1. factorial\n"); /*' 1.팩토리얼' 출력*/
    printf("2. sin\n"); /* 2.사인 출력*/
    printf("3. log(base10)\n"); /* 3.로그 (base 10) 출력*/
    printf("4. square root\n"); /* 4.제곱근 출력*/
    printf("5. permutation(nPr)\n"); /* 5.순열 출력*/
    printf("6. combination(nCr)\n"); /* 6.조합 출력*/
    printf("7. End\n"); /* 7.종료 출력*/
    printf("Please Select: "); /* '선택하시오' 출력*/
    scanf("%d", &n); /*원하는 번호 (정수=d) 입력*/
    return n; /* 사용자가 선택한 값 반환*/
}

void factorial() /*팩토리얼을 계산하는 함수 출력*/
{
    long long n, result = 1, i; /*long long n, result=1, i 세 개의 변수 선언*/
    printf("정수를 입력하시오: "); /*'정수를 입력하시오' 출력*/
    scanf("%lld", &n); /*사용자가 정수를 입력하게 함*/
    for (i = 1; i <= n; i++)
        result = result * i; /*for문을 사용한 팩토리얼 값 계산, 만약 i가 n보다 작거나 같을 경우 i는 계속 증가, 결과는 결과값 * 1로 계산 */
                      
    printf("결과 = %lld\n\n", result); /*결과값 출력*/
}


void sine() /*사인 값을 계산하는 함수 출력*/
{
    double a, result; /*변수 double(실수 데이터 저장하기 위한 자료형) a(각도 저장), result 선언*/
    printf("각도를 입력하시오: "); /*사용자에게 각도를 입력하라는 문구 출력*/
    scanf("%lf", &a); /*사용자가 각도 입력*/
    result = sin(a); /*사인값 계산*/
    printf("결과 = %lf\n\n", result); /*결과 출력*/
}


void longBase10() /*밑이 10인 로그 값을 계산하는 함수 선언*/
{
    double a, result; /*변수 2개 double a, result 선언*/
    printf("실수값을 입력하시오: "); /*사용자에게 실수값을 입력하라는 문구 출력*/
    scanf("%lf", &a); /*사용자가 실수 값 입력함*/
    if (a <= 0.0) /*만약 a가 0.0보다 작거나 같다면*/
        printf("오류\n"); /*'오류'로 출력됨*/
    else /*아니라면 (if-else)구문*/ 
    {
        result = log10(a); /*밑이 10인 로그 값 계산*/
        printf("결과 = %lf\n\n", result); /*결과 값 출력*/
    }
}

int main(void) /*메인함수 호출*/
{
    while (1) {
        switch (menu()) {
            case 1:
                factorial(); /*만약 사용자가 메뉴 1번을 선택한다면, 팩토리얼을 계산*/ 
                break; /*break를 걸어줌으로써 다음 case를 실행하지 못 하게 함. (switch-break)문 */
                
            case 2:
                sine(); /* 만약 사용자가 케이스 2번을 선택한다면 사인값을 계산하는 함수 호출*/
                break; /*break를 걸어줌으로써 다음 case를 실행하지 못 하게 함*/
                
            case 3:
                longBase10(); /* 만약 사용자가 케이스 3을 선택한다면,밑이 10인 로그 값 계산 함수 호출*/
                break; /*break를 걸어줌으로써 다음 case를 실행하지 못 하게 함*/
                
            case 7:
                printf("종료합니다.\n"); /*만약 사용자가 7번을 선택한다면 '종료합니다'라는 문구 출력*/
                return 0; /*0으로 초기화 및 프로그램 정상 종료*/
                
            default:
                printf("잘못된 선택입니다.\n"); /* 메뉴 1-7 외에 다른 번호를 선택할 경우 '잘못된 선택'이라는 문구 출력*/
                break; /*break를 걸어줌으로써 다른 case를 실행하지 못 하게 함*/
        }
    }
}
```
 
 
