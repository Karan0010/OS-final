#include<stdio.h>

struct job{
	int par;
	int amv;
	int bts;
	int cmds;
	int attr;
}f[200], s[200], m[200];

int n, fc=0, sc=0, mc=0;
int quanti;

void roundRobin(){
	int time= m[0].amv, mark=0, cc=0, i, rc;
	while(time!=120 && cc!=mc){
		for(i=0; i<=mark; i++){
			if(m[i].attr > quanti){
				time += quanti;
				m[i].attr -= quanti;
			}
			else if(m[i].attr <=quanti && m[i].attr !=0){
				time += m[i].attr;
				m[i].attr =0;
				m[i].cmds = time;
				cc++;
			}
			else;
		}
		int start = mark+1;
		for(rc= start; rc<mc; rc++){
			if(m[rc].amv <= time){
				mark++;
			}
		}
	}	
}

void merger(){
	int isc=0, ifc= 0, min, flag;
	if( fc!=0  && sc!=0){
		while(isc<sc && ifc<fc){
			if(f[ifc].amv == s[isc].amv){
				m[mc] = f[ifc];
				mc++;
				ifc++;
				m[mc]= s[isc];
				mc++;
				isc++;
			}
			else if(f[ifc].amv < s[isc].amv){
				m[mc]= f[ifc];
				mc++;
				ifc++;
			}
			else if(f[ifc].amv > s[isc].amv){
				m[mc]= s[isc];
				mc++;
				isc++;
			}
			else;
		}
		if(mc != (fc+sc)){
			if(fc!=ifc){
				while(ifc!=fc){
					m[mc]= f[ifc];
					mc++;
					ifc++;
				}
			}
			else if(sc!=isc){
				while(isc!=sc){
					m[mc]= s[isc];
					mc++;
					isc++;
				}
			}
		}
	}
	else if(fc==0){
		while(isc!=sc){
			m[mc]= s[isc];
			mc++;
			isc++;
		}
	}
	else if(sc==0){
		while(ifc!=fc){
			m[mc]= f[ifc];
			mc++;
			ifc++;
		}
	}
	else {
		printf("\n No valid Jobs available\n");
	}
}

void printer(){
	int i=0, total=0, sum=0; 
	double avg;
	printf("\nSummary for the Execution\n");
	printf("\nQuery ID\tArrival Time\tRessolving Time\tCompletion Time\tTurn Around Time\tWaiting Time");
	for(i; i<mc; i++){
		printf("\n%d\t\t%d\t\t%d\t\t%d\t\t%d\t\t\t%d",
		m[i].par, (m[i].amv+1000), m[i].bts, (m[i].cmds+1000), (m[i].cmds-m[i].amv), ((m[i].cmds-m[i].amv)- m[i].bts));
		total= m[i].cmds;
		sum+= (m[i].cmds-m[i].amv);
	}
	avg = sum/mc;
	printf("\n\nTotal time Spent for all queries: %d", total);
	printf("\nAverage query time: %lf", avg);
	printf("\nProcess Execution Complete");
}

void input(){
	int map,  i, t;
	printf("Enter total no of queries: "); scanf("%d", &n);
	if(n==0) { printf("\n No queries\n"); }
	else{
		printf("\nEnter quantity for each Process: "); scanf("%d", &quanti);
		printf("\nEnter 1 for faculty and 2 for student\n");
		for(i=0; i<n; i++){
			printf("\nJob Type (1/2): "); scanf("%d", &map);
			if(map==1){
				printf("Query Id: "); scanf("%d", &f[fc].par);
				printf("Arrival Time: "); scanf("%d", &t);
				if(t<1000 || t>1200){
					printf("\nEnter Correct time");
					input();
				}
				else{f[fc].amv= t-1000;}
				printf("Resolving Time: "); scanf("%d", &f[fc].bts);	 f[fc].attr= f[fc].bts; 
				fc++;
			} else{
				printf("Query Id: "); scanf("%d", &s[sc].par);
				printf("Arrival Time: "); scanf("%d", &t); 
				if(t<1000 || t>1200){
					printf("\nEnter Correct time\n");
					input();
				}
				else {s[sc].amv= t-1000; }
				printf("Resolving Time: "); scanf("%d", &s[sc].bts);	 s[sc].attr= s[sc].bts;
				sc++;
			}
		}
	}
}

void inst(){
	printf("\nWelcome,Please follow these instruction"
			"\n**>Enter time in 2400 hours format. example for 11:30 am enter 1130"
			"\n**>Enter Query arrival times in ascending order\n"
			"\nAll Time units are in minutes. \n\n"
			);
}

 main(){
 	inst();
	input();
	merger();
	roundRobin();
	printer();
}
