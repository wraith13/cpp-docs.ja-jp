---
title: Concurrency 名前空間演算子 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: e2957aa84ffbf420dcf2672359a442b754866649
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180415"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 名前空間演算子 (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>  operator==

指定した引数が等しいかどうかを判断します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
比較するタプルの 1 つ。

*_Rhs*<br/>
比較するタプルの 1 つ。

### <a name="return-value"></a>戻り値

**true**タプルが、それ以外の場合は**false**します。

##  <a name="operator_neq"></a>  operator!=

指定した引数が等しくないかどうかを判断します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
比較するタプルの 1 つ。

*_Rhs*<br/>
比較するタプルの 1 つ。

### <a name="return-value"></a>戻り値

**true**タプルが、それ以外の場合**false**します。

##  <a name="operator_add"></a>  operator+

指定された引数の要素ごとの合計を計算します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
追加する引数の 1 つ。

*_Rhs*<br/>
追加する引数の 1 つ。

### <a name="return-value"></a>戻り値

指定された引数の要素ごとの合計。

##  <a name="operator-"></a>  operator-

指定された引数の要素ごとの差を計算します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
減算元の引数。

*_Rhs*<br/>
減算する引数。

### <a name="return-value"></a>戻り値

指定された引数の要素ごとの差。

##  <a name="operator_star"></a>  operator*

指定された引数の要素ごとの積を計算します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
乗算するタプルのいずれか。

*_Rhs*<br/>
乗算するタプルのいずれか。

### <a name="return-value"></a>戻り値

指定された引数の要素ごとの積。

##  <a name="operator_div"></a>  operator/

指定された引数のコンポーネントごとの商を計算します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
除算されるタプル。

*_Rhs*<br/>
除算するタプル。

### <a name="return-value"></a>戻り値

指定された引数のコンポーネントごとの商。

##  <a name="operator_mod"></a>  operator%

2 番目の指定された引数による 1 番目の指定された引数の剰余を計算します。

```
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
タプルの引数のランク。

*_Lhs*<br/>
剰余が計算される元のタプル。

*_Rhs*<br/>
それによって剰余が計算されるタプル。

### <a name="return-value"></a>戻り値

2 番目の指定された引数による 1 番目の指定された引数の剰余という結果。

## <a name="see-also"></a>関連項目

[同時実行 Namespace ](concurrency-namespace-cpp-amp.md)
