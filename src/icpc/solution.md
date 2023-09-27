# Previous ICPC Dhaka Regional Solutions  
# 2022
# D. Omicron Juice
== "C++"
   ```cpp
   #include <iostream>
   using namespace std;

   int main(){
	   int t;
	   cin>>t;
	   for(int i=1;i<=t;i++)
	  {
		    int a,b,c,k;
	    	cin>>a>>b>>c>>k;
		    cout<<"Case "<<i<<": ";
		    if(a==b && b==c){
			       cout<<"Peaceful\n";
			       continue;
		    }
	     	if((k>a && k>b) || (k>b && k>c) || (k>a && k>c))
		           cout<<"Fight";
		    else if((a+b+c)%3 !=0)
		           cout<<"Fight";
		    else
		   {
			      int m=(a+b+c)/3;
		       	a=(a-m)%k;
		       	b=(b-m)%k;
		      	c=(c-m)%k;
		      	if(a!=0 || b!=0 || c!=0)
			             cout<<"Fight";
		      	else
			             cout<<"Peaceful";
		   }
	     	cout<<"\n";
	    }
     }
```
