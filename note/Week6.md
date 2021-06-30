## 程式的編譯、組譯、連結、載入之流程 ##
    高階語言 -> 編譯器 -> 組合語言 -> 組譯器 ->目的檔 -> 連結器 -> 執行檔 -> 載入器 -> 記憶體
## power2.c ##
    #include <stdio.h>

    int power2(int n) {
        if (n==0) ruturn 1;
        return power2(n-1)*2;
    }
    int main(){
        int p = power2(3);
        printf("p=%d\n", p);
    }
    執行:
    gcc power2.c -o power2
    ./power2
    p=8
