---
title: "Jak można debugować naruszenia dostępu C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d3eed91a659dc8f0d114369bdba45dd2973375
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Jak można debugować naruszenia dostępu C++
## <a name="problem-description"></a>Opis problemu  
 Program tworzy naruszenia zasad dostępu. Jak debugować to?  
  
## <a name="solution"></a>Rozwiązanie  
 Jeśli w wierszu kodu, który wyłuskań wielu wskaźniki naruszenia zasad dostępu, może być trudne dowiedzieć się, które wskaźnika spowodował naruszenie zasad dostępu. Począwszy od programu Visual Studio 2015 Update 1 wyjątków — okno dialogowe teraz jawnie nazwy wskaźnika, który spowodował naruszenie zasad dostępu.  
  
 Przykładowo podana następujący kod, należy pobrać naruszenia zasad dostępu:  
  
```C++  
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
  
 Po uruchomieniu tego kodu w programie Visual Studio 2015 Update 1 powinny zostać wyświetlone następujące okno dialogowe wyjątek:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Jeśli nie można ustalić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, śledzenia przez kod, aby upewnić się, że wskaźnik przyczyną problemu został poprawnie przypisany.  Jeśli został przekazany jako parametr, upewnij się, że jest przekazywany poprawnie i nie są tworzone przypadkowo [skrócona kopiowania](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Następnie sprawdź, czy wartości są nie przypadkowo zmieniane gdzieś w programie tworząc upewnij się, że nie są modyfikowane w innym miejscu w programie danego punktu przerwania danych wskaźnika. Aby uzyskać więcej informacji na temat punkty przerwania danych, zobacz sekcję punktu przerwania danych w [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)