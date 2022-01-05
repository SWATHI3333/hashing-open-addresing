#include<stdio.h>
#include<stdlib.h>
int hash(int x)
{
    return x%10;
}
void insert(int *a,int x)
{
  int i=hash(x),flag=0,j;
  if(a[i]==-1)
  {
      a[i]=x;
      flag=1;
  }
  else
  {
      for(j=i+1;j<10;j++)
      {
          if(a[j]==-1)
          {
              a[j]=x;
              flag=1;
              break;
          }
      }
  }
  for(j=0;j<i&&flag==0;j++)
  {
    if(a[j]==-1)
    {
        a[j]=x;
        flag=1;
        break;
    }
  }
  if(flag==0)
  {
      printf("No place to insert");
  }
}
void display(int *a)
{
    int i;
    for(i=0;i<10;i++)
    {
        printf("%d ",a[i]);
    }
}
void delete(int *a,int x)
{
    int i=hash(x),flag=0,j;
    if(a[i]==x)
    {
        a[i]=-1;
        flag=1;
    }
    else
    {
        for(j=i+1;j<10;j++)
        {
            if(a[j]==x)
            {
                a[j]=-1;
                flag=1;
                break;
            }
        }
       
       
    }
    for(j=0;j<i&&flag==0;j++)
    {
        if(a[j]==x)
        {
            a[j]=-1;
            flag=1;
            break;
        }
    }
    if(flag==1)
        {
            printf("Element %d is deleted",x);
        }
        else
        {
            printf("Element is not found");
        }
}
void search(int *a,int x)
{
    int i=hash(x),flag=0,j,pos;
    if(a[i]==x)
    {
        flag=1;
        pos=i;
    }
    else
    {
        for(j=i+1;j<10;j++)
        {
            if(a[j]==x)
            {
                flag=1;
                pos=j;
                break;
            }
        }
    }
    for(j=0;j<i&&flag==0;j++)
    {
        if(a[j]==x)
        {
            flag=1;
            pos=j;
            break;
        }
    }
    if(flag==1)
    {
        printf("%d ele is present at %d",x,pos+1);
    }
    else
    {
        printf("ele is not present");
    }
}
void main()
{
    int c,a[10],i,x;
    for(i=0;i<10;i++)
    {
        a[i]=-1;
    }
    while(1)
    {
    printf("enter choice 1.insert 2.delete 3.serch 4.display 5.exit");
    scanf("%d",&c);
    switch(c)
    {
        case 1:
               printf("enter ele to insert");
               scanf("%d",&x);
               insert(a,x);
               break;
       case 2:
               printf("enter ele to delete");
               scanf("%d",&x);
               delete(a,x);
               break;
        case 3:
              printf("enter ele to search");
               scanf("%d",&x);
               search(a,x);
               break;
        case 4:
              display(a);
              break;
        case 5:
              exit(1);
        default:printf("Enter correct number");
               
    }
    }
}
