---
layout:     post
title:      "Hash Tables: Ice Cream Parlor"
subtitle:   "Golang의 Map을 활용한 알고리즘 풀이"
date:       2019-01-27
author:     "Hotpotato00"
URL: "/2019/01/27/ctci-ice-cream-parlor/"
image:      "img/home-bg-jeep.jpg"
tags:        ["hackerrank", "golang"]
categories:  ["Tech"]
---

Hash Tables: Ice Cream Parlor

> 먼저 [문제](https://www.hackerrank.com/challenges/ctci-ice-cream-parlor/problem "ice-cream")의 요지는 다음과 같다.

> **t번**의 상황에 대해 맛이 **n개**인 **아이스크림**이 주어진다. 이 때 각 맛에 따라 가격 *(Cost)* 이 다르고, 주어지는 돈 *(Money)* 으로 살 수 있는 맛이 몇 번째 맛인지 그 *index*를 구하는 것이 문제의 요지.

해당 링크.<https://www.hackerrank.com/challenges/ctci-ice-cream-parlor/problem/>

처음에는 당연히 이중 for문을 이용해서 풀었으나, 당연히 *Fail*

>그래서 [Hackerrank](https://www.hackerrank.com "hackerrank")의 가장 큰 장점인 [Discussions](https://www.hackerrank.com/challenges/ctci-ice-cream-parlor/forum )을 활용하였고,
[Two-Sum](https://leetcode.com/articles/two-sum/)이란 *Hash-Map* 활용한 알고리즘을 확인할 수 있었다.

```go
func whatFlavors(cost []int32, money int32) {
    flavorsMap := make(map[int32]int)
    for i := range cost {
      f1 := money - cost[i]
      // Golang의 Map에 key 존재 여부
      if _, ok := flavorsMap[f1] ; ok {
        fmt.Printf("%d %d\n", flavorsMap[f1]+1, i+1)
      }
      flavorsMap[cost[i]] = i
    }
}
```
