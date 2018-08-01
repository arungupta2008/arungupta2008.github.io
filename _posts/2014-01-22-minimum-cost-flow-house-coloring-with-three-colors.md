---
id: 244
title: 'Minimum cost flow  House coloring with three colors'
date: 2014-01-22T15:57:02+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=244
permalink: /?p=244
dsq_thread_id:
  - "2157767362"
categories:
  - Algorithm
  - C or C++
tags:
  - Algorithm
  - Coding
---
There are a row of houses, each house can be painted with three colors red, blue and green. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color. You have to paint the houses with minimum cost. How would you do it?

Note: Painting house-1 with red costs different from painting house-2 with red. The costs are different for each house and each color.

Approach:
  
Dynamic Programming solution:
  
we can paint the i&#8217;th house with blue, red or green.

<pre>Enter No. of Houses to paint : 6
1 4 5
1 3 9
6 7 2
9 6 4
3 5 2
6 7 4

Minimum Cost to paint all houses are 20
</pre>

<pre class="brush: cpp; title: ; notranslate" title="">#include &lt;stdio.h&gt;
#include &lt;stdarg.h&gt;
#define COLOR 3
#define MAX(a,b) ((a) &gt; (b) ? a : b)
#define MIN(a,b) ((a) &lt; (b) ? a : b)
#define R 0
#define B 1
#define G 2
#define Color 3


int min( int num, ... )
{
    va_list arguments;
    int min=0;
    int tmp=0;
    /* Initializing arguments to store all values after num */
    va_start ( arguments, num );
    /* Sum all the inputs; we still rely on the function caller to tell us how
     * many there are */
    min = va_arg ( arguments, int );
    //printf("\n1st|%d|\n",min);
    for ( int x = 1; x &lt; num; x++ )
    {
		tmp = va_arg(arguments,int);
		min = MIN(min,tmp);
    }
    va_end ( arguments );
    // Cleans up the list
	//printf("\nMin is %d", min);
    return min;
}
typedef struct {
    int  color;
    int cost;
    //struct nodee *root;
}node;
int main()
{
	node cost[3];
	int house = 3;
	printf("Enter No. of Houses to paint : ");
	scanf("%d",&house);
	int color[house][COLOR];
//	int ji=0;
	for(int i=0; i&lt;house;++i){
		for(int j=0; j&lt;COLOR;++j){
				scanf("%d",&color[i][j]);
//				color[i][j]= ++ji;
			}

		}
	//cost[0].cost=color[0][R];cost[1].cost=color[0][B];cost[2].cost=color[0][G];
	for(int i= 0; i&lt; Color ;i++){
			cost[i].cost=color[0][i];
			cost[i].color = i;
		} // Initial Submission of values, and colour
//	printf("\nA.cost\t%d(%d)\tB.cost\t%d(%d)\tC.cost\t%d(%d)\n",cost[0].cost,cost[0].color,cost[1].cost,cost[1].color,cost[2].cost,cost[2].color);
	//A.color = R; B.color = B; C.color = G;
	int tmp_B=0,tmp_G=0,tmp_R=0;
	//printf("\nR_cost\t%d\tB_cost\t%d\tG_cost\t%d\n",R_cost,B_cost,G_cost);
	for(int i=1; i&lt;house;++i)
		{
			for(int j= 0; j&lt; Color ;j++){
				if(cost[j].color == R){
						if(color[i][B] &lt; color[i][G]){
							cost[j].cost = cost[j].cost + color[i][B];
							cost[j].color = B;
							//add_linked_list();
							//cost[j].root = malloc(sizeof(struct node));
							//cost[j].root-&gt;next = 0;
							//cost[j].root-&gt;x = color[i][B];
						}else{
								cost[j].cost = cost[j].cost + color[i][G];
								cost[j].color = G;
						}
					}else if(cost[j].color == B){
							if(color[i][R] &lt; color[i][G]){
								cost[j].cost = cost[j].cost + color[i][R];
								cost[j].color = R;
							}else{
									cost[j].cost = cost[j].cost + color[i][G];
									cost[j].color = G;
								}
						}else{
								//Case for G
								if(color[i][R] &lt; color[i][B]){
									cost[j].cost = cost[j].cost + color[i][R];
									cost[j].color = R;
									}else{
											cost[j].cost = cost[j].cost + color[i][B];
											cost[j].color = B;
										}
							}
//			printf("\nA.cost\t%d(%d)\tB.cost\t%d(%d)\tC.cost\t%d(%d)\n",cost[0].cost,cost[0].color,cost[1].cost,cost[1].color,cost[2].cost,cost[2].color);
			}
			/*
			if(A.color == )
			//R_cost = min(2,color[i][B],color[i][G])+R_cost;
			if(color[i][B] &lt; color[i][G]){

				tmp_B = R_cost + color[i][B];
				}else{
						tmp_G = R_cost + color[i][G];
					}

			//B_cost = min(2,color[i][R],color[i][G])+B_cost;
			if(color[i][R] &lt; color[i][G]){

				tmp_R = B_cost + color[i][R];
				}else{
						tmp_G = B_cost + color[i][G];
					}
			//G_cost = min(2,color[i][B],color[i][R])+G_cost;
			if(color[i][R] &lt; color[i][B]){

				tmp_R = G_cost + color[i][R];
				}else{
						tmp_B = G_cost + color[i][B];
					}
			R_cost = tmp_R;
			B_cost = tmp_B;
			G_cost = tmp_G;
			//printf("\n G %d:%d",color[i][B],color[i][R]);
			*/
//			printf("\nA.cost\t%d(%d)\tB.cost\t%d(%d)\tC.cost\t%d(%d)\n",cost[0].cost,cost[0].color,cost[1].cost,cost[1].color,cost[2].cost,cost[2].color);
		}
	printf("\nMinimum Cost to paint all houses are %d\n",min(3,cost[0].cost,cost[1].cost,cost[2].cost));
}

</pre>