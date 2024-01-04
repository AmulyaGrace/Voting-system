#include<stdio.h>
#include <conio.h>
#include <string.h>
#include <stdlib.h>
int main() {
printf("WELCOME TO ELECTION SYSTEM!!!!!");
FILE *f;
char ch;
char sentence[1000];
char votername[100];
char regno[100];
while(1) {
struct candidate {
char name[80];
int votes;
int cno;
} c[100];
int n;
f=fopen("feedback.txt","w");
fclose(f);
printf("\nNo of candidates:");
scanf("%d", &n);
for (int i=0; i<n; i++) {
printf("\nCandidate name:\n");
scanf("%s", &c[i].name);
c[i].cno=i;
c[i].votes=0;}
while(1) {
printf("\nBEGIN THE VOTING, TYPE 0 TO FINISH VOTING
PROCESS\n");
for (int i=0; i<n; i++) {
printf("Candidate number %d, %s\n", c[i].cno+1, c[i].name);}
int d;
int t=3;
while(t!=0) {
printf("\nSelect candidate number to vote\n");
scanf("%d", &d);
for(int i=0; i<n; i++) {
if(d-1==c[i].cno) {
c[i].votes++;
printf("\n");
f=fopen("feedback.txt","a");
fgets(votername, sizeof(votername), stdin);
fprintf(f, "%s", votername);
printf("Registration no:");
fgets(regno, sizeof(regno), stdin);
fprintf(f, "%s\n", regno);
fprintf(f, "%s\n", c[i].name);
printf("Please specify your reasons for voting
this candidate");
fgets(sentence, sizeof(sentence), stdin);
fprintf(f, "%s\n", sentence);
fclose(f);
} else if(d==0) {
t=0;
break;
}
}
}
for (int i=0; i<n; i++) {
printf("\nCANDIDATE NAME %s, VOTES %d\n", c[i].name,
c[i].votes);
}
printf("\n1.Continue Voting\n2.Collect all votes\n");
int b;
printf("\nSelect option:\n");
scanf("%d", &b);
if(b==1) {
continue;
} else if(b==2) {
break;
}
}
return 0;
}
