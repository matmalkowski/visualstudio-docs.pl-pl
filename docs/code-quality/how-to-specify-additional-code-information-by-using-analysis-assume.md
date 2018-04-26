---
title: 'Porady: określanie informacji o dodatkowym kodzie za pomocą __analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 181f9fb4a1f9f5d653d64fb813b974bad898fe13
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Porady: określanie informacji o dodatkowym kodzie za pomocą __analysis_assume
Musisz podać wskazówki narzędzie do analizy kodu dla kodu C/C++, który będzie pomocy procesu analizy i zmniejszyć ostrzeżenia. Aby podać dodatkowe informacje, należy użyć następującej funkcji:

 `__analysis_assume(`  `expr`  `)`

 `expr` -Dowolne wyrażenie, które przyjęto, że mogła zwrócić wartość true.

 Narzędzie do analizy kodu zakłada, że reprezentowanego przez wyrażenie warunku jest wartość true w momencie, gdy funkcja pojawia się i pozostaje wartość true, dopóki wyrażenie jest zmieniony, na przykład przez przypisanie do zmiennej.

> [!NOTE]
>  `__analysis_assume` nie ma wpływu optymalizacji kodu. Poza narzędzie do analizy kodu `__analysis_assume` jest zdefiniowany jako pusta.

## <a name="example"></a>Przykład
 Poniższy kod używa `__analysis_assume` Aby naprawić kod analizy ostrzeżenia [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  __analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Zobacz też
 [__assume](/cpp/intrinsics/assume)