---
title: 'Porady: eksport cieniowania'
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8975bbff3e845f0bee66f5c0e27f9935d1986593
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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

     **Program do cieniowania pikseli HLSL (\*.hlsl)** eksportuje programu do cieniowania jako wysoki poziom cieniowania języka (HLSL) kodu źródłowego. Ta opcja umożliwia modyfikowanie programu do cieniowania później, nawet po nie została wdrożona w aplikacji. To może ułatwić debugowania i poprawki kodu na podstawie problemów użytkowników końcowych, ale także ułatwi dla użytkownika do modyfikacji programu do cieniowania w sposób niechciane — na przykład, aby uzyskać korzyści nieuczciwej konkurencji gry. On również może zwiększyć czas ładowania programu do cieniowania.

     **Skompilowany program do cieniowania pikseli (\*.cso)** eksportuje jako HLSL kodu bajtowego programu do cieniowania. Ta opcja powoduje, że jest możliwe do modyfikacji programu do cieniowania później, nawet po nie została wdrożona w aplikacji. To może ułatwić debugowania i poprawki kodu na podstawie problemów przez użytkownika końcowego, ale ponieważ programu do cieniowania jest wstępnie skompilowanym, go nie nakładu dodatkowe środowiska uruchomieniowego podczas ładowania programu do cieniowania przez aplikację. Wystarczająco doświadczeni użytkownicy mogą modyfikować programu do cieniowania w sposób niepożądane, ale kompilowania programu do cieniowania sprawia, że to znacznie trudniejsze.

     **Nagłówek C++ (\*.h)** eksportuje jako nagłówek stylu języka C, który definiuje tablicę bajtów zawierającą HLSL kodu bajtowego programu do cieniowania. Ta opcja może być bardziej czasochłonne, debugowania i poprawki kodu opartego na problemy przez użytkownika końcowego, ponieważ aplikacja musi ponownie skompilowana, aby przetestować tę poprawkę. Jednak ponieważ ta opcja utrudnia, chociaż nie jest to niemożliwe zmodyfikować programu do cieniowania po jego wdrożeniu w aplikacji, stanowi większość trudności, użytkownikowi, który chce się zmodyfikować programu do cieniowania w sposób niepożądane.

4.  W **nazwę pliku** pola kombi, określ nazwę programu do cieniowania wyeksportowany, a następnie wybierz **zapisać** przycisku.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)