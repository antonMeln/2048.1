#include <iostream>
using namespace std;
int cn[4][4];
void initmas(int u[4]){
    for(int i=0;i<4;i++){u[i]=0;}
}
void init(){
    cn[1][0]=4;
    cn[1][1]=2;
    cn[1][2]=2;
    cn[1][3]=2;
    cn[2][3]=4;
    cn[0][3]=2;
    cn[2][2]=4;
}
bool up(int uper[4][4]){
    bool any=true;

    for(int j=0;j<4;j++)
      {int y[4];initmas(y);int n=0;
        for(int i=0;i<4;i++)
        {if(uper[j][i]!=0)
          {y[n]=uper[j][i];n++;}}

        for(int z=0;z<4;z++)
             {if((y[z]==y[z+1])&&(y[z]!=0))
                 {y[z]+=y[z+1];y[z+1]=0;}}

      for(int w=0;w<3;w++)
        {if(y[w]==0)
         {y[w]=y[w+1];y[w+1]=0;}}

        for(int i=0;i<4;i++)
          {uper[j][i]=y[i];};
        }

    return any;
}
bool down(int uper[4][4]){
    bool any=true;

    for(int j=0;j<4;j++)
    {int y[4];initmas(y);int n=3;
        for(int i=3;i>-1;i--)
        {if(uper[j][i]!=0)
          {y[n]=uper[j][i];n--;}}

        for(int z=3;z>0;z--)
        {if((y[z]==y[z-1])&&(y[z]!=0))
          {y[z]+=y[z-1];y[z-1]=0;}}

        for(int w=3;w>0;w--)
            {if(y[w]==0)
              {y[w]=y[w-1];y[w-1]=0;}}

        for(int i=0;i<4;i++)
           {uper[j][i]=y[i];};
    }

    return any;
}
bool left(int uper[4][4]){
    bool any=true;

    for(int j=0;j<4;j++)
       {int y[4];initmas(y);int n=0;
        for(int i=0;i<4;i++)
          {if(uper[i][j]!=0)
            {y[n]=uper[i][j];n++;}}

        for(int z=0;z<4;z++)
           {if((y[z]==y[z+1])&&(y[z]!=0))
               {y[z]+=y[z+1];y[z+1]=0;}}

        for(int w=0;w<3;w++)
            {if(y[w]==0)
               {y[w]=y[w+1];y[w+1]=0;}}

        for(int i=0;i<4;i++)
           {uper[i][j]=y[i];};
    }


    return any;
}
bool right(int uper[4][4]){
    bool any=true;
    for(int j=0;j<4;j++)
      {int y[4];initmas(y);int n=3;
        for(int i=3;i>-1;i--)
           {if(uper[i][j]!=0){y[n]=uper[i][j];n--;}}

        for(int z=3;z>0;z--)
           {if((y[z]==y[z-1])&&(y[z]!=0))
             {y[z]+=y[z-1];y[z-1]=0;}}

        for(int w=3;w>0;w--)
           {if(y[w]==0)
             {y[w]=y[w-1];y[w-1]=0;}}

        for(int i=0;i<4;i++)
           {uper[i][j]=y[i];};
    }


    return any;
}
void bmpout(){
    for(int j=0;j<4;j++){
        for(int i=0;i<4;i++){
            if(cn[i][j]==0){cout<<"*"<<" ";continue;}cout<<cn[i][j]<<" ";
        } cout<<"\n";
    }
    cout<<"\n";
}
int main() {char com=' ';
    init();

    while(com!='q'){

        switch(com){
            case 'j':
                down(cn);
                break;
            case 'k':
                up(cn);
                break;
            case 'h':
                left(cn);
                break;
            case 'l':
                right(cn);
                break;

        }
        bmpout();
        cin>>com;
    }
    return 0;
}
