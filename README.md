#include<iostream>
#include<vector>
 
using namespace std;
 
class Matrix{
    public:
        Matrix operator+(Matrix);
        Matrix operator-(Matrix);
        friend ostream& operator<<(ostream &out,Matrix x);
        friend istream& operator>>(istream &in,Matrix x);
private:
        vector< vector<int> > arr;
        int n,m;
};
 
ostream& operator<<(ostream &out,Matrix x){
    for(int i=0;i<x.n;i++){
        for(int j=0;j<x.m;j++)
            out<<x.arr[i][j]<<" ";
        out<<endl;
    }
    out<<x.m<<" "<<x.n;
return out;
}
 
istream& operator>>(istream &in,Matrix x){
    in>>x.n;
    in>>x.m;
    int a;
    for(int i=0;i<x.n;i++){
        vector<int> row;
        for(int j=0;j<x.m;j++){
            in>>a;
            row.push_back(a);
        }
        x.arr.push_back(row);
    }
return in;
}
 
Matrix Matrix::operator+(Matrix a){
    Matrix tmp;
    for(int i=0;i<arr.size();i++){
        vector<int> row;
        for(int j=0;j<arr[i].size();j++)
            row.push_back(arr[i][j]+a.arr[i][j]);
        tmp.arr.push_back(row);
    }
return tmp;
}
 
Matrix Matrix::operator-(Matrix a){
    Matrix tmp;
    for(int i=0;i<arr.size();i++){
        vector<int> row;
        for(int j=0;j<arr[i].size();j++)
            row.push_back(arr[i][j]-a.arr[i][j]);
        tmp.arr.push_back(row);
    }
return tmp;
}
 
int main(void){
    Matrix a;
    cin>>a;         
    cout<<a;
    system("Pause");
    return 0;
}
