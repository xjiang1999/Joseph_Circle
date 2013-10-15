Joseph_Circle
=============


#include<iostream>
using namespace std;
typedef struct Lnode{
    int data;
    struct Lnode *next;
}*Linklist;
void joseph(int n,int m,int *p){
    Linklist a,b,c=NULL;
    int i;
    for(i=1;i<=n;i++){
        a=(Linklist)malloc(sizeof(Lnode));
        a->data=i;
        if(c==NULL){
            b=a;
            c=a;
        }
        else{
            b->next=a;
            b=a;
        }
    }
    a->next=c;
    a=c;//建立循环链表完毕
    for(i=0;i<m-1;i++){//指针移向第一个报数人的位置
        b=a;
        a=a->next;
    }
    cout<<a->data<<" ";//输出第一个报数人
    int q=a->data;//记录第一个报数人，等会要用到其密码值
    b->next=a->next;
    free(a);
    a=b->next;
    while(a->next!=a){
        for(i=0;i<p[q-1]-1;i++){
            b=a;
            a=a->next;
        }
        cout<<a->data<<" ";
        q=a->data;
        b->next=a->next;//删除结点a
        free(a);
        a=b->next;
    }
    cout<<a->data;
}

int main(){
    int n,p[100],m;
    while(cout<<"number of the people:"<<endl && cin>>n && n!=0){
        cout<<"passwords:"<<endl;
        for(int i=0;i<n;i++)
            cin>>p[i];
        cout<<"value of the 'm':"<<endl;
        cin>>m;
        joseph(n,m,p);
        cout<<endl;
        cout<<"-----------------"<<endl;
    }
    return 0;
}
