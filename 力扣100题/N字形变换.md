### 1. 找到规律，本质上是对s字符串的重新排列；  
### 2. 即每一行对应于s中第几位；  
//原形状
>P   A   H   N  
>A P L S I I G  
>Y   I   R  

//带index
>P(base=i)   A(base=base+2n-2)   H..   N..  
>A(base=i(i+1)) P(base+(2n-2i-2)) L(base=base+2n-2) S I I G  
>Y(base=i(i+2))   I..   R..  


## 3. 规律即：  
### 1. 以每一行的行数作为每一行开头的base基地址在s中进行索引，并在第一列base与下一列base中间如果有多余的字母进行append（除了第一行跟最后一行不需要）；2. base列中间的字母索引为base+(2n-2i-2)，通过一般例子推演；3. base列与base列的字母索引关系为base+2n-2；4. 注意边界条件，其他都可以了  
---
### 代码块：  
```C
class Solution {
public:
    string convert(string s, int numRows) {
        string res;
        int base;
        if (s.size()==1 || numRows>s.size() || numRows==1)
            return s;
        res="";
        for(int i=0;i<numRows;i++){
            base=i;
            while( base<=s.size()-1){
                res+=s[base];
                if((base+2*numRows-2-2*i)<=s.size()-1 && i!=0 && i!=numRows-1){
                    res+=s[base+2*numRows-2-2*i];
                }
                base+=2*numRows-2;
            }
        }
        return res;
    }
};
```