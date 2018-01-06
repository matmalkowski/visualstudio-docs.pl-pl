---
title: 'Porady: eksportowanie programu do cieniowania | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6b4c7cedd267ba02772db16e026803061933cf5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-shader"></a>Porady: eksport cieniowania
Ten dokument pokazano, jak wyeksportować cieniowania skierowane wykres programu do cieniowania języka (DGSL) może być używany w aplikacji za pomocą projektanta programu do cieniowania.  
  
 W tym dokumencie przedstawiono tego działania:  
  
-   Eksportowanie do cieniowania  
  
## <a name="exporting-a-shader"></a>Eksportowanie do cieniowania  
 Po utworzeniu programu do cieniowania przy użyciu narzędzia Projektant programu do cieniowania i przed użyciem w aplikacji, należy go wyeksportować w formacie, który rozumie graficznego interfejsu API. Na różne sposoby do różnych celów, możesz wyeksportować programu do cieniowania.  
  
#### <a name="to-export-a-shader"></a>Aby wyeksportować do cieniowania  
  
1.  W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz **Visual wykres programu do cieniowania (dgsl)** pliku.  
  
     Jeśli nie masz **Visual wykres programu do cieniowania (dgsl)** pliku do otwierania, utwórz je zgodnie z opisem w [porady: Tworzenie podstawowego cieniowania kolor](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Na **Designer programu do cieniowania** narzędzi wybierz **zaawansowane**, **wyeksportować**, **Eksportuj jako**. **Eksportu programu do cieniowania** zostanie wyświetlone okno dialogowe.  
  
3.  W **Zapisz jako typ** listy rozwijanej wybierz format, który ma zostać wykonane eksportowanie.  
  
     Poniżej przedstawiono formatów, które użytkownik może:  
  
     **Program do cieniowania pikseli HLSL (\*.hlsl)**  
     Eksportuje programu do cieniowania jako wysoki poziom cieniowania języka (HLSL) kodu źródłowego. Ta opcja umożliwia modyfikowanie programu do cieniowania później, nawet po nie została wdrożona w aplikacji. To może ułatwić debugowania i poprawki kodu na podstawie problemów użytkowników końcowych, ale także ułatwi dla użytkownika do modyfikacji programu do cieniowania w sposób niechciane — na przykład, aby uzyskać korzyści nieuczciwej konkurencji gry. On również może zwiększyć czas ładowania programu do cieniowania.  
  
     **Skompilowany program do cieniowania pikseli (\*.cso)**  
     Eksportuje programu do cieniowania w postaci kodu bajtowego HLSL. Ta opcja powoduje, że jest możliwe do modyfikacji programu do cieniowania później, nawet po nie została wdrożona w aplikacji. To może ułatwić debugowania i poprawki kodu na podstawie problemów przez użytkownika końcowego, ale ponieważ programu do cieniowania jest wstępnie skompilowanym, go nie nakładu dodatkowe środowiska uruchomieniowego podczas ładowania programu do cieniowania przez aplikację. Wystarczająco doświadczeni użytkownicy mogą modyfikować programu do cieniowania w sposób niepożądane, ale kompilowania programu do cieniowania sprawia, że to znacznie trudniejsze.  
  
     **Nagłówek C++ (\*.h)**  
     Eksportuje programu do cieniowania jako nagłówek stylu języka C, który definiuje tablicę bajtów zawierającą kodu bajtowego HLSL. Ta opcja może być bardziej czasochłonne, debugowania i poprawki kodu opartego na problemy przez użytkownika końcowego, ponieważ aplikacja musi ponownie skompilowana, aby przetestować tę poprawkę. Jednak ponieważ ta opcja utrudnia, chociaż nie jest to niemożliwe zmodyfikować programu do cieniowania po jego wdrożeniu w aplikacji, stanowi większość trudności, użytkownikowi, który chce się zmodyfikować programu do cieniowania w sposób niepożądane.  
  
4.  W **nazwę pliku** pola kombi, określ nazwę programu do cieniowania wyeksportowany, a następnie wybierz **zapisać** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie cieniowania kolor podstawowy](../designers/how-to-create-a-basic-color-shader.md)   
 [Projektant cieniowania](../designers/shader-designer.md)