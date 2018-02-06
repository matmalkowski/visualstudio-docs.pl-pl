---
title: "Generuj komentarze dokumentacji XML dla języka Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Generuj komentarze dokumentacji XML w Visual Basic

**Co:** pozwala natychmiast wygenerować base XML wymagane do dokumentu wybranego elementu. 

**Kiedy:** chcesz utworzyć komentarzy dokumentu XML do późniejszego przetwarzania przez dokumentacji narzędzia, takiego jak Sandcastle.

**Dlaczego:** można ręcznie utworzyć blok komentarza całego samodzielnie, ale spowoduje to zaoszczędzić czas i zwiększyć dokładność, generując podstawowego szablonu i dodatkowych elementów. 

**Jak:**

1. Umieść kursor nad elementem chcesz dokumentu, na przykład metoda tekstu.

   ![Metoda do dokumentu](media/doc-highlight-vb.png)

1. Następnie wpisz **'''** (3 pojedynczy cudzysłów) które automatycznie utworzy szablon podstawowy i wszelkie dodatkowe elementy w razie potrzeby.  Na przykład podczas dodawania komentarzy metody, generuje  **\<podsumowania\>**  tagi, jak również  **\<param\>**  tagu dla każdego parametru, który jest przekazywany do metody, a  **\<zwraca\>**  tag do dokumentu, metoda zwraca.

   ![Szablon](media/doc-preview-vb.png)

1. Wypełnij komentarze i Dodaj wszelkie dodatkowe informacje, które można to konieczne.

   ![Komentarz ukończone](media/doc-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Dokumentowanie kodu za pomocą XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Generowanie kodu](../code-generation-in-visual-studio.md)