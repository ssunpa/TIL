# Responsive Units

## 사이즈를 결정하는 unit

-   `Absolute` : 절대적 사이즈, 컨테이너 사이즈가 변경되어도 고정 값으로 유지
    ex)`px`...
      <aside>
      💡 모니터 위에서 화면에 나타낼 수 있는 가장 작은 단위를 px(픽셀)이라 한다.
      
      </aside>

-   `Relative` : 상대적 사이즈
    ex)`em`,`rem`...

<aside>
💡 브라우저는 기본적으로 16px로 설정된다.

</aside>

## em

relative to parent element, 부모 사이즈에 상대적

```css
.parent {
    font-size: 8em;
}
.child {
    font-size: 0.8em;
}
```

<img src="./img/em_result.png" width="300"/>

결과 값

parent의 8em = 16px \* 8 = 128px

child의 0.5em = 128px \* 0.5 = 64px

## rem

relative to root element, 최고 루트 사이즈에 상대적

```css
.parent {
    font-size: 8rem;
}
.child {
    font-size: 0.8rem;
}
```

<img src="./img/rem_result.png" width="300"/>

결과 값

parent의 8rem = 16px \* 8 = 128px

child의 0.5rem = 16px \* 0.5 = 8px
