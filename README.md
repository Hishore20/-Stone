# -Stone


Roman has no idea, why this problem is called Stone. He also has no idea on how to solve the following problem: given array of N integers A and a number K. During a turn the maximal value over all Ai is chosen, lets call it MAX. Then Ai =MAX - Ai is done for every 1 <= i <= N. Help Roman to find out how will the array look like after K turns.

Input
The numbers N and K are given in the first line of an input. Then N integers are given in the second line which denote the array A.
Output
Output N numbers on a single line. It should be the array A after K turns.
Constraints
1 <= N <= 105
0 <= K <= 109
Ai does not exceed 2 * 109 by its absolute value
Logic Test Case 1

Input (stdin)
4 1

5 -1 7 0

Expected Output

2 8 0 7
Logic Test Case 2

Input (stdin)
5 1

5 -1 7 2 0

Expected Output

2 8 0 5 7





#include <stdio.h>
typedef long long int LLI;
#define inchar getchar_unlocked
inline int inIntNeg() {
	int n=0, ch, neg=0;
	while ((ch = inchar()) < 32);
	if(ch=='-') neg=1;
	else n= (ch - '0');
	while((ch = inchar()) >= '0') {
		n = (n << 3) + (n << 1) + (ch - '0');
	}
	return neg?-n:n;
}

#define MAX_N 100000
LLI a[MAX_N];
int n;

void iterate() {
	LLI ma;
	int i;
	ma=a[0];
	for(i=1; i<n; ++i) if(a[i]>ma) { ma=a[i]; }
	for(i=0; i<n; ++i) a[i] = ma-a[i];
}

void print() {
	int i;
	printf("%lld",a[0]); for(i=1; i<n; ++i) printf(" %lld",a[i]); printf("\n");
}

int main() {
	int k,i;

	n = inIntNeg();
	k = inIntNeg();

	for(i=0; i<n; ++i) a[i] = inIntNeg();

	if( k > 0) {
		iterate();
		if((k&1)==0) iterate();
	}
	print();
	return 0;
}
