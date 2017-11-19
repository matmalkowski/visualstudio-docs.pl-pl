---
title: "Porady: ograniczanie Instrumentacji do określonych funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fae944ae73c3bfdfdf278b9b905ebab06ba3ff1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Porady: ograniczanie instrumentacji do określonych funkcji
Można ograniczyć Instrumentacji i gromadzenia danych do co najmniej jedną funkcję przez ustawienie opcji **zaawansowane** strony **sesji wydajności** lub docelowego stron właściwości binarnej:  
  
-   Jeśli określisz funkcje na stronie właściwości sesji wydajności, tylko te funkcje są instrumentowane w instrumentowanych danych binarnych na sesji.  
  
-   Jeśli określisz funkcje na stronie właściwości obiektu docelowego, binary, tylko funkcje będące w tym są instrumentowane określonego pliku binarnego. Funkcje w innych plikach binarnych wydajności działają normalnie.  
  
 Ograniczenie zbierania danych w ten sposób jest obsługiwana tylko w przypadku wybrania metoda profilowania instrumentacji.  
  
> [!NOTE]
>  Można również użyć **zaawansowane** strony **sesji wydajności** strony właściwości można ustawić inne opcje, które są dostępne dla narzędzi profilowania [VSInstr](../profiling/vsinstr.md) wiersza polecenia Narzędzie instrumentacji.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Ograniczenie Instrumentacji do określonych funkcji w sesji wydajności  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji, a następnie kliknij przycisk **właściwości**.  
  
     **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  Na **strony właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
3.  W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni, aby wpisać nazwę funkcji, które mają być dokumentu:  
  
     **/ include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
     `FuncSpec`jest to nazwa przestrzeni nazw i funkcji. Ma format `Namespace` **::**`FunctionName`. Użyj średnika, aby oddzielić wiele funkcji. Użyj gwiazdki (\*) można określać symboli wieloznacznych dla co najmniej jeden znak. Na przykład **/ include: MyNS::\***  określa wszystkich funkcji w obszarze nazw MyNS.  
  
    > [!NOTE]
    >  Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnego narzędzi profilowania (zazwyczaj \Team Tools\Performance katalogu narzędzia w obszarze [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] katalog instalacyjny), a następnie wpisz **vsinstr / DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Ograniczenie Instrumentacji do określonych funkcji w pliku binarnym  
  
1.  W **Eksplorator wydajności**, zlokalizuj Nazwa binarna w **cele** węzła sesji wydajności.  
  
2.  Kliknij prawym przyciskiem myszy nazwa pliku binarnego, a następnie kliknij przycisk **właściwości**.  
  
     **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
3.  Na **strony właściwości** okno dialogowe, kliknij przycisk **zaawansowane**.  
  
4.  W **dodatkowych opcji Instrumentacji** tekst pola, użyj następującej składni, aby wpisać nazwę funkcji, które mają być dokumentu:  
  
     **/ include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
     `FuncSpec`jest to nazwa przestrzeni nazw i funkcji. Ma format `Namespace` **::**`FunctionName`. Użyj średnika, aby oddzielić wiele funkcji. Użyj gwiazdki (\*) można określać symboli wieloznacznych dla co najmniej jeden znak. Na przykład **/ include: MyNS::\***  określa wszystkich funkcji w obszarze nazw MyNS.  
  
    > [!NOTE]
    >  Aby wyświetlić listę funkcji w pliku binarnym, Otwórz okno wiersza polecenia w katalogu instalacyjnego narzędzi profilowania (zazwyczaj \Team Tools\Performance katalogu narzędzia w obszarze [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] katalog instalacyjny), a następnie wpisz **vsinstr / DumpFuncs**  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Porady: ograniczanie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Porady: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)