#include <stdio.h>

int main(void)
{
    int delay;
    int homework;
    int deadline;
    int score = 0;

    printf("====================================\n");
    printf("       미래의 나 고소장 생성기\n");
    printf("====================================\n\n");

    printf("현재의 나에게 묻겠습니다.\n\n");

    printf("일을 미룬 시간은 몇 시간인가요? : ");
    scanf_s("%d", &delay);

    printf("남은 과제는 몇 개인가요? : ");
    scanf_s("%d", &homework);

    printf("마감까지 며칠 남았나요? : ");
    scanf_s("%d", &deadline);

    // 피해 점수 계산
    score = delay * 2 + homework * 3;

    if (deadline <= 2)
    {
        score = score + 5;
    }

    // 판결 결과 출력
    printf("\n====================================\n");
    printf("             최종 판결\n");
    printf("====================================\n");

    printf("피고인 : 현재의 나\n");
    printf("피해자 : 미래의 나\n");
    printf("피해 점수 : %d점\n\n", score);

    if (score >= 30)
    {
        printf("판결 : 중형 선고!\n");
        printf("미래의 나에게 심각한 피해를 주었습니다.\n");
        printf("지금 당장 모든 일을 시작하세요!\n");
    }
    else if (score >= 20)
    {
        printf("판결 : 유죄!\n");
        printf("미래의 나에게 큰 피해를 주었습니다.\n");
        printf("더 이상 미루지 마세요!\n");
    }
    else if (score >= 10)
    {
        printf("판결 : 집행유예!\n");
        printf("아직 기회가 있습니다.\n");
        printf("오늘부터 조금씩 시작하세요!\n");
    }
    else
    {
        printf("판결 : 무죄!\n");
        printf("미래의 나를 잘 배려하고 있습니다.\n");
        printf("지금처럼 꾸준히 진행하세요!\n");
    }

    printf("\n====================================\n");
    printf("       재판을 종료합니다.\n");
    printf("====================================\n");

    return 0;
}
