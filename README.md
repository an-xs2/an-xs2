
#include <stdio.h>

typedef struct recommend { char place[30]; int time; }Recommend;

void ShowAry(int* pa, int size) //두 날짜 사이에 있는 것까지 배열에 저장 { int x = 0; for (int i = 0; i < 2; i++) { int a = 0, b = 0; scanf_s("%d %d", &a, &b); for (int j = a; j <= b; j++) { pa[x] = j; x++; }//날짜 배열 } }

extern char s1[500]; extern char s2[500]; extern char s3[500]; extern char s4[500]; extern char s5[500]; extern char s6[500];

int main(void) { int mem1[30] = { 0, }; int mem2[30] = { 0, }; int mem3[30] = { 0, }; int sum1[30] = { 0, }; int sum2[30] = { 0, };

int i, j;
int k = 0;
int n;
int p_num;
int num = 0;
int len1 = 0;
int len2 = 0;
int len3 = 0;
int len4 = 0;

printf("인원 수를 선택하세요. : ");
scanf_s("%d", &n);
start:

if (n == 2)
{
	printf("사람 1 : ");
	ShowAry(mem1, 30);
	printf("사람 2 : ");
	ShowAry(mem2, 30);
}

if (n == 3)
{
	printf("사람 1 : ");
	ShowAry(mem1, 30);
	printf("사람 2 : ");
	ShowAry(mem2, 30);
	printf("사람 3 : ");
	ShowAry(mem3, 30);

	while (mem3[len3] != 0)
	{
		len3++;
	}
}

while (mem1[len1] != 0)
{
	len1++;
}

while (mem2[len2] != 0)
{
	len2++;
}

for (i = 0; i < len1; i++)
{
	for (j = 0; j < len2; j++)
	{
		if (mem1[i] == mem2[j])
		{
			num++;
			sum1[num - 1] = mem2[j];
		}
	}
}

if (n == 3)
{
	for (i = 0; i < num; i++)
	{
		for (j = 0; j < len3; j++)
		{
			if (sum1[i] == mem3[j])
			{
				k++;
				sum2[k - 1] = mem3[j];
			}
		}
	}
}

if (num == 0)
{
	printf("여행 가능한 날이 없습니다.\n날짜를 다시 입력해주세요.\n");
	goto start;
}

else
{
	if (n == 2)
	{
		printf("여행 가능한 날 : ");
		for (i = 0; i < num; i++) {
			for (j = 0; j < num; j++) {
				if (sum1[i] == sum1[j + 1]) {
					for (int k = 0; k < num - j; k++, j++) {
						sum1[j + 1] = sum1[j + 2];
					}
				}
			}
		}

		for (i = 0; i < num; i++)
			if (sum1[i] != 0)
				printf("%d일 ", sum1[i]); //출력
	}
	else if (n == 3)
	{
		printf("여행 가능한 날 : ");
		for (i = 0; i < k; i++) 
		{
			for (j = 0; j < k; j++)
			{
				if (sum2[i] == sum2[j + 1])
				{
					for (int l = 0; l < num - j; l++, j++)
					{
						sum2[j + 1] = sum2[j + 2];
					}
				}
			}
		}
		for (i = 0; i < k; i++)
			if (sum2[i] != 0)
				printf("%d일 ", sum2[i]); //출력
	}
}

printf("\n\n\n");
printf(" 1.부산\n 2.강원도\n 3.전주\n 4.서울\n 5.경주\n 6.제주\n");
printf("여행 가고 싶은 지역을 선택해 주세요. :  ");
scanf_s("%d", &p_num);
printf("\n\n");

Recommend p1 = { "부산",4 };
Recommend p2 = { "강원도",2 };
Recommend p3 = { "전주",3 };
Recommend p4 = { "서울",1 };
Recommend p5 = { "경주",4 };
Recommend p6 = { "제주",4 };

switch (p_num)
{
case 1: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p1.place, s1, p1.time);
	break;
case 2: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p2.place, s2, p2.time);
	break;
case 3: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p3.place, s3, p3.time);
	break;
case 4: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p4.place, s4, p4.time);
	break;
case 5: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p5.place, s5, p5.time);
	break;
case 6: printf(" 지역 : %s\n 추천 관광지 : %s\n 소요시간 : %d", p6.place, s6, p6.time);
	break;
}
return 0;
}
