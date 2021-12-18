#include <stdio.h>
#include <stdlib.h>
#include<stdbool.h>
int main(void) {
  //N為總人數
  //M為總割菜數
  int M=0;
  unsigned long long int N=0;
  int cnt_N,cnt_M;
  unsigned long long int i=0;
  int cnt_k=1;
  int bool_i, bool_j;
  unsigned long long int interval_A=0, interval_b=0; //區間
  int k1=0,k2=0;
  unsigned long long int k1_MA=0,k2_MA=0,k1_MB=0,k2_MB=0;
  int output=0;
  //輸入總人數
  printf("please type how many people\n");
  scanf("%lld", &N);
  //判斷值域範圍
  if (N>999999999999)
    printf("Sorry the number's scope from 0 to 999999999");
  else if(N<=999999999999 && N>1000000)
    k1=N/1000000; //第一區>1000000
    k2=N%1000000; //第二區<1000000
  else 
    k1=0;
    k2=N%1000000;
  bool leek[k1+1][k2+1]; //切成2個區塊 999999作為分界線
  
  

  //韭菜原先都有持幣的狀況下 
  //分做兩區填充true值
  for(bool_i=0;bool_i<=k1;bool_i++){
    for(bool_j=0;bool_j<100000;bool_j++)
    leek[bool_i][bool_j] = 'true'; 
    }
    for(bool_j=0;bool_j<k2+1;bool_j++)
    leek[k1][bool_j]='true';
//輸入割韭菜次數
  printf("plese enter how many times to cut leek\n");
  scanf("%d\n", &M);
  //執行M次割韭菜行為
  for(cnt_M=0;cnt_M<M;cnt_M++)
  {
    //輸入每次割韭菜區間
    printf("please enter the interval\n");
    scanf("%lld %lld\n",&interval_A, &interval_b);
    k1_MA=interval_A/1000000;
    k2_MA=interval_A%1000000;
    k1_MB=interval_b/1000000;
    k2_MB=interval_b%1000000;
    //進行每次割韭菜行為
    for(bool_i=k1_MA;bool_i<=k1_MB;bool_i++)
      for(bool_j=k2_MA;bool_j<=k2_MB;bool_j++)
      leek[bool_i][bool_j]=leek[bool_i][bool_j]*(-1);
  }

  for(bool_i=0;bool_i<=k1;bool_i++){
    for(bool_j=0;bool_j<=k2;bool_j++)
    if(leek[bool_i][bool_j])
    output+=output;
  }
  printf("%d", output);

}
