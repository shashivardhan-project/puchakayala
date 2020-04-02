
    #include <stdio.h>
    #define min(A,B) ((A) > (B) ? (B) : (A))
    #define max(A,B) ((A) > (B) ? (A) : (B))
    int main(void)
	{
		int m,n,w  ,x=0, p, r, k,i,nc,rc,dc,cw,time;
    	int ca[50];
    	int br[5100];       
		printf("enter no of cars : ");  
    	scanf("%d",&n);
    	printf("enter no of people wandering in park : ");  
    	scanf("%d", &w);
    	printf("enter ride time : ");  
    	scanf("%d", &p);
    	printf("enter after how much time passenger comes to ride gate : ");  
    	scanf("%d", &r);
    	printf("enter how much time park opens : ");  
    	scanf("%d", &k);  
    		if (n == 0)
			{
    			int movedToReady = min(w, k/r);
    			printf("0 0 %d %d\n", w - movedToReady, x + movedToReady);
    		}
    		dc = rc = 0;
    		for (i = 0; i < n; i++)
    			ca[i] = 0;
    		m = w+x;
    		for (i = x; i < m; i++)
    			br[i] = (i-x+1)*r;
     
    		nc = 0;
    		for (i = 0; i < m; i++){
    			int readyTime = br[i];
    			if (readyTime > k)
    				break;
    			
    			if (ca[nc] > readyTime)
    				readyTime = ca[nc];
    			ca[nc] = readyTime + p;
    			nc = (nc+1) % n;
     
    			if (readyTime + p <= k)
    				dc++;
    			else if (readyTime <= k)
    				rc++;
    		}
     
    		cw = 0;
    		for (i = 0; i < n; i++)
    			if (ca[i] <= k)
    				cw++;
    		int a=max(0, w - k/r);
    		 int b=x + min(w, k/r) - dc - rc;
    		 int c=a+b;
    		 int d=w-dc-c;
    		printf("%d cars are at gate now\n", cw  /n);
    		printf("%d passangers completes the ride \n" ,dc);
    		printf("%d passangers doesnt get a ride\n", c);
    		printf("%d passengers are in a ride", d);
    	return 0;
    } 
