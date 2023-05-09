# Number-of-Coins

	int solve(int v, int n, int coin[], int i, vector<vector<int>>&dp)
	{
	   // if(i==n-1)
	   // {
	   //     if(v==coin[i] || v==0) return 1;
	   //     return 0;
	   // }
	    if(v==0)
	    {
	        //pair<bool, int>p={true,1};
	        return 0;//possible 
	    }
	    
	    if(i>=n)
	    {
	       // pair<bool, int>p={false,-1};
	        return INT_MAX;
	    }
	    
	    if(dp[v][i]!=-1)
	    {
	        return dp[v][i];
	    }
	    
	    long long int t=INT_MAX;
	    if(v-coin[i]>=0)
	    {
	        t=1LL+solve(v-coin[i],n,coin,i,dp);
	    }
	    long long int n1=solve(v,n,coin,i+1,dp);
	    
	    return dp[v][i]=min(t,n1);
	    
	    
	}
	
	int minCoins(int coins[], int M, int V) 
	{
	    vector<vector<int>>dp(V+1, vector<int>(M+1, -1));
	    
	    if(solve(V,M,coins,0,dp)==INT_MAX)
	    {
	        return -1;
	    }
	    return solve(V,M,coins,0,dp);
	    
	    // Your code goes here
	} 
	  
