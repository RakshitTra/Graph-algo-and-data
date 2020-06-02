#include<bits/stdc++.h>
using namespace std;
vector<int> adj[1005];
vector<int> Ctree[1005];
bool vis[1005];
int gg=0;
//############ its for size ################
int dfs(int root,int p){
    int sum=1;
    for(auto v:adj[root]){
        if(v!=p&&!vis[v]){
            sum+=dfs(v,root);
        }
    }
    return sum;
}
//############## centroid return formula ###########################
int dfs1(int root,int p,int siz){
    for(auto v:adj[root]){
        if(v!=p&&!vis[v]){
            int val=dfs(v,root);
            if(val>siz/2)return dfs1(v,root,siz);
        }
    }
    return root;
}
//###################### form a decomposed subtree###########################################
int cent_decom(int root,int p){
    int siz=dfs(root,p);
    //cout<<"root here is "<<root<<" and size of tree"<<siz<<endl;
    int centroid=dfs1(root,p,siz);
    //cout<<"its centroid"<<centroid<<endl;
    vis[centroid]=true;
    for(auto v:adj[centroid]){
        if(!vis[v]){
            int cent=cent_decom(v,centroid);
            //cout<<"subchild of decomposed tree"<<cent<<endl;
            Ctree[centroid].push_back(cent);
        }
    }
    return centroid;
}
int main(){
    int i,j,n;
    cin>>n;
    for(i=0;i<n-1;i++){
        int u,v;
        cin>>u>>v;
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
    memset(vis,false,sizeof(vis));
    int cen=cent_decom(1,0);
    for(i=1;i<=n;i++){
        cout<<"This are the child of ith node in decomposed tree"<<" "<<i<<endl;
        for(auto v:Ctree[i]){
            cout<<v<<" ";
        }
        cout<<endl;
    }
    return 0;

}
