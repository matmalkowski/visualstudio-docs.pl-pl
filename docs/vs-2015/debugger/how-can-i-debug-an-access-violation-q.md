---
title: Jak można debugować naruszenia zasad dostępu? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c06121d84c6b573b5f1895fa447535826dad540
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678444"
---
# <a name="how-can-i-debug-an-access-violation"></a>Jak można debugować naruszenia zasad dostępu?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [w jaki sposób można debugować naruszenia zasad dostępu?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-an-access-violation-q).  
  
Opis problemu  
 Program powoduje naruszenie zasad dostępu. W jaki sposób można to debugować?  
  
## <a name="solution"></a>Rozwiązanie  
 Jeśli w wierszu kodu, który wyłuskań wielu wskaźników naruszenie zasad dostępu, może być trudne dowiedzieć się, wskaźnika, który spowodował naruszenie zasad dostępu. Począwszy od programu Visual Studio 2015 Update 1, okno dialogowe wyjątku teraz jawnie nazwy wskaźnika, który spowodował naruszenie zasad dostępu.  
  
 Na przykład biorąc pod uwagę następujący kod, należy uzyskać naruszenie zasad dostępu:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
        ClassC* C;  
        ClassB() {  
                C = new ClassC();  
        }  
     void printHello() {  
                cout << "hello world";  
        }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
      ClassA() {  
                B = nullptr;  
        }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
      A->B->printHello();  
}  
```  
  
 Jeśli uruchomisz ten kod w Visual Studio 2015 Update 1, powinny zostać wyświetlone następujące okno dialogowe wyjątku:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Jeśli nie można ustalić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, prześledzi kod, aby upewnić się, że wskaźnik przyczyną problemu jest poprawnie przypisany.  Jeśli został przekazany jako parametr, upewnij się, że jest prawidłowo przekazane i nie są przypadkowe tworzenie [skrócona kopiowania](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Następnie sprawdź, czy wartości są nie przypadkowo zmieniane gdzieś w programie, tworząc upewnij się, że nie są modyfikowane w innym miejscu w programie dany punkt przerwania danych zostanie wskaźnika. Aby uzyskać więcej informacji na temat punkty przerwania danych, zobacz sekcję punktu przerwania danych w [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)



