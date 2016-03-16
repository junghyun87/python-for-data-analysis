## A Brief matplotlib API primer
### Figures and Subplots
* Figure object안에 plots이 있음.
* plt.figure()로 figure object 생성
* plt.gcf()로 active figure에 대한 reference 얻기
* fig.gca()로 active subplot에 대한 reference 얻기
* blank figure에는 plot을 못만듬. fig.add_subplot으로 subplots을 추가해야함.
* plt.plot으로 plot을 그리면 사용된 마지막 figure의 subplot에 plot을 그린다. 이전에 그린 plot이 있으면 그 위에 겹쳐서 그려진다.
``` python
#example
plt.plot(randn(50).cumsum(),'k--')
```
* fig.add_subplot은 AxesSubplot objects를 리턴. 이 objects로 plot을 그리면 해당 subplot에 그려짐.
``` python
#example
ax1 = fig.add_subplot(2,2,1)
ax1.hist(randn(100), bins=20, color='k', alpha=0.3)
```
* plt.plot으로 plot을 그리면 바로 plotting되는데 AxesSubplot objects로 plot을 그리면 바로 안됨. 이유는? plt.draw()하면 바로 반영됨.
* fig, axes = plt.subplots(2,3)으로 한번에 여러 subplot objects 생성.
* 처음에 axe references가 없더라도 fig.get_axes()로 AxesSubplot objects에 접근할 수 있음.

#### Adjusting the spacing around subplots
plt.subplots_adjust로 subplots 간에 space 조절

### Colors, Markers, and Line Styles
help(plt.plot)으로 linestyle, marker 등 어떤 parameter 사용할 수 있는지 알수있음.

### Ticks, Labels, and Legends
* plot decorations에는 pyplot interface를 사용한 방법과 object-oriented native matplotlib API를 사용한 방법이 있다.
* pyplot interface를 사용한 방법은 interactive한 방법으로 적용하면 바로 plot에 반영된다. 예를들면, plt.xlim([0,10])과 같은 함수. 모든 함수는 active하거나 가장 최근에 생성된 AxesSubplot에 적용된다.
* 두번째 방법은 subplot object의 set, get함수를 이용하는 것. 예를들면, ax.get_xlim, ax.set_xlim. 특정 subplot에 명시적으로 decorations을 적용할 수 있음.

### Saving Plots to File
* plt.savefig('figpath.png') 를 하면 active figure가 저장됨.

## Plotting Functions in pandas
* 대부분 pandas's plotting methods는 ax parameter를 accept한다. 따라서 원하는 subplot에 plot을 배치할 수 있음


