#### <i class="icon-file"></i>程式結果說明
>此程式模擬玩家進行賠率為1:1得下注方式(如猜紅黑,奇偶,大小)  
一次1單位的賭資 下注n次後 最後淨輸贏的結果。  
此程式提供**:**   
1.模擬的線圖      
2.淨輸贏的期望值  
3.由95%得信心水準所構成的淨輸贏區間  

ps.因為俄羅斯輪盤有 "0" 這個格子  
所以賠率為1:1時，勝率為18/37≒0.4864 < 0.5

#### <i class="icon-file"></i>程式碼說明

>: n = int(raw_input("n=?"))  
t = np.arange(n)  
由使用者輸入下注的次數  
並由 np.arange(n)建立 [1,2,3.....t] 的數列

>result = [1,-1]  
x=np.random.choice(result,n,p=[0.4864,0.5136])  
ts=np.cumsum(x)   
由 np.random.choice()  模擬每回合的輸贏  
分別以 0.4864,0.5136的機率傳回1(贏)或-1(輸)  
由 np.cumsum() 建立由累積每次輸贏的時間序列資料 存在 ts 中

>由二項分配公式得出每回合淨輸贏金額的期望值和標準差 mean ,sigma

>由 plt.fill_between() 畫出由95%信賴區間所構成的淺黃色區域  

ps.信賴區間:  
上界:(t*0.4864-2*sigmat)*1 + (t-(t*0.4864-2*sigmat))*-1  
下界:(t*0.4864+2*sigmat)*1 + (t-(t*0.4864+2*sigmat))*-1  
sigmat 為由t=1,t=2,t=3....t=n時的標準差構成的數列

#### <i class="icon-file"></i>實測 

>當輸入n=10000 得出此圖  

https://hostr.co/bv2chTDuQ7Lq
