# priority-Circulare-Queue

#include<bits/stdc++.h>
#include<conio.h>

using namespace std;

class stud{
	public:
		int rno;
		int priority;
		stud *next;
};

void display(stud *q,int start,int end,int n){
	if(start == -1){
		cout<<"Underflow"<<endl;
		return;
	}
	else{
		for(int i=start;i!=end;i = (i+1)%n)
			cout<<q[i].rno<<"-"<<q[i].priority<<" -> ";
		cout<<q[end].rno<<"-"<<q[end].priority<<" -> "<<endl;
	}
}

void push(stud *q,int &start,int &end,int n,int data,int priority){
	if((end+1)%n == start)
		cout<<"Overflow";
	else if(end == -1){
		start = 0;
		end = 0;
		q[end].rno = data;
		q[end].priority = priority;
	}
	else{
		end = (end+1)%n;
		q[end].rno = data;
		q[end].priority = priority;
		int l = 0;
		for(int i = start;i!=end;i=(i+1)%n,l++);
		int i = end,j;
		while(l--){
			if(i-1 == -1) j=n-1;
			else j = i-1;
			if(q[j].priority < q[i].priority){
				swap(q[j].rno,q[i].rno);
				swap(q[j].priority,q[i].priority);
				i = j;
			}
			else
				break;
		}
	}
}

void pop(stud *q,int &start,int &end,int n){
	if(end == start){
		start = -1;
		end = -1;
	}
	start = (start+1)%n;
}

int main(){
	int n = 5;
	int start =-1,end = -1; 
	stud *q = new stud[n];
	for(int i=1;i<=n;i++){
		q[i-1].next = &q[(i%n)-1];	 
	}	
	return 0;
}

/*push(q,start,end,n,1,0);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,2,0);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,3,1);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	pop(q,start,end,n);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,4,2);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,5,1);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	pop(q,start,end,n);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,6,3);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,7,2);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();
	
	push(q,start,end,n,8,4);
	display(q,start,end,n);
	cout<<start<<" "<<end<<endl;
	getch();*/
