//.cpp : Defines the entry point for the console application.
//
#include "string.h"
#include <stdio.h>

char *WEEK[7] = { "星期天", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六" };

struct demand {
	char name[5];
	int day[7];
} man[7];


int main() {
	int IsChecked(int p[]);
	int  t = 0, j, ren[7];
	long i, k;
	printf("**湖南邮电移动205班每日排课系统**\n");
	printf("请各位老师分别输入各自合适的休假日\n");
	printf("如方旋老师的C语言课程，休息日期选择星期二和星期三,就输入2 3 然后回车\n");
	printf("数字0 1 2 3 4 5 6分别代表\n星期天 星期一 星期二 星期三 星期四 星期五 星期六\n");
	printf("注意要输入星期天请输入数字0 \n");

	for (i = 0; i < 7; i++) {
		printf("请第%d个人输入\n", i + 1);

		for (k = 0; k < 7; k++) {
			//scanf("%d",&man[i].day[k]);
			char c;
			scanf("%c", &c);

			if (c == '\n') {
				break;//读取到换行符，即回车，退出循环。
			} else if (c >= 48 && c <= 57) {
				man[i].day[k] = (int)(c - '0');
				//printf("%d %c\n", k, c);
			} else if (c == ' ') {
				k--;
			}
		}

		// printf("你输入的day是:");
		// for(k=0;k<7;k++)
		// {
		//     printf("%d ",man[i].day[k]);
		// }
		// printf("\n");

		printf("你输入的day是:");

		for (int m = 0; m < k; m++) {
			printf("%d ", man[i].day[m]);
		}

		for (int m = k; m < 7; ++m) {
			man[i].day[m] = 8;
			printf("%d ", man[i].day[m]);
		}

		printf("\n");
	}

	printf("****************************************************************************************************");
	printf("\n*  C语言编程,    IP网络技术,    LTE网络,    通信电源,  体育课   ,    国学智慧,    音乐鉴赏 ,  *\n");
	printf("*------------------------------------------------------------------------------------------------*\n");
	printf("");

	for (i = 0; i < 2097152; ++i) {
		for (j = 0; j < 7; ++j) {
			ren[j] = (i >> (3 * j)) & 7; //*通过这个循环，穷尽0-7在数组中所有的排列组合方式*//
		}

		if (!(ren[0] == man[0].day[0] || ren[0] == man[0].day[1] || ren[0] == man[0].day[2] || ren[0] == man[0].day[3]
		        || ren[0] == man[0].day[4] || ren[0] == man[0].day[5] || ren[0] == man[0].day[6]))
			continue;//*如果C语言编程不是休周二或周四，就不用循环了。*//
		else if (!(ren[1] == man[1].day[0] || ren[1] == man[1].day[1] || ren[1] == man[1].day[2] || ren[1] == man[1].day[3]
		           || ren[1] == man[1].day[4] || ren[1] == man[1].day[5] || ren[1] == man[1].day[6]))
			continue; //*如果IP网络技术不是休周一或周六，就不用循环了。*//
		else if (!(ren[2] == man[2].day[0] || ren[2] == man[2].day[1] || ren[2] == man[2].day[2] || ren[2] == man[2].day[3]
		           || ren[2] == man[2].day[4] || ren[2] == man[2].day[5] || ren[2] == man[2].day[6]))
			continue; //*如果LTE网络不是休周三或周日，就不用循环了。*//
		else if (!(ren[3] == man[3].day[0] || ren[3] == man[3].day[1] || ren[3] == man[3].day[2] || ren[3] == man[3].day[3]
		           || ren[3] == man[3].day[4] || ren[3] == man[3].day[5] || ren[3] == man[3].day[6]))
			continue; //*如果通信电源不是休周五，就不用循环了。*//
		else if (!(ren[4] == man[4].day[0] || ren[4] == man[4].day[1] || ren[4] == man[4].day[2] || ren[4] == man[4].day[3]
		           || ren[4] == man[4].day[4] || ren[4] == man[4].day[5] || ren[4] == man[4].day[6]))
			continue; //*如果体育课不是休周一或周四或周六，就不用循环了。*//
		else if (!(ren[5] == man[5].day[0] || ren[5] == man[5].day[1] || ren[5] == man[5].day[2] || ren[5] == man[5].day[3]
		           || ren[5] == man[5].day[4] || ren[5] == man[5].day[5] || ren[5] == man[5].day[6]))
			continue; //*如果国学智慧不是休周二或周五，就不用循环了。*//
		else if (!(ren[6] == man[6].day[0] || ren[6] == man[6].day[1] || ren[6] == man[6].day[2] || ren[6] == man[6].day[3]
		           || ren[6] == man[6].day[4] || ren[6] == man[6].day[5] || ren[6] == man[6].day[6]))
			continue; //*如果音乐鉴赏不是休周三或周六或周日，就不用循环了。*//
		else if (!IsChecked(ren))
			continue; //*至此，所有邮电老师可按他们的愿望休假，但是此时的方案可能有两个人同休一天的*//

		//*情况发生，因此用这个函数排除，如果0-6这七个数字（一周七天）任何一个包含在数组中则此次匹配失败。*//
		for (j = 0; j < 7; ++j) {
			printf("%s ", WEEK[ren[j]]);
		}

		printf("   *");
		printf("\n");  //*输出成功匹配方案*//
		++t;  //*记录成功匹配个数*//
	}


	printf("*--------------------------------------------*");
	printf("\n*          %d 种 情 况!               *", t); //*输出成功匹配方案个数*//
	printf("\n**********************************************");
	getchar();
	return 0;
}


int IsChecked(int p[]) {
	int i, j;

	for (i = 0; i < 7; ++i) {
		for (j = 0; j < 7 && p[j] != i; ++j); /*从0到6循环，如果数组中缺少0-6的任何一位数字，则返回0，如果0-6都有，则返回。*/

		if (j == 7)
			return 0;
	}

	return 1; //*这个函数的作用是确保0-6这7个数字均包含在该数组中*//
}
