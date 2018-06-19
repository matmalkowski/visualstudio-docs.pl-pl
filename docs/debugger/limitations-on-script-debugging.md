---
title: Ograniczenia debugowania skryptu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6679e781e564a58d6a98b7d0190f2f2b4e9fa74
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476838"
---
# <a name="limitations-on-script-debugging"></a>Ograniczenia debugowania skryptu
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obsługuje debugowanie skryptu po stronie klienta, może ulec ograniczenia w tym temacie.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Ograniczenia dotyczące mapowanie punktów przerwania z skryptu po stronie klienta  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można ustawić punktu przerwania w pliku po stronie serwera ASPX lub HTML, który jest przekształcany na plik po stronie klienta w czasie wykonywania. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mapuje przerwania z pliku po stronie serwera w celu odpowiedniego punktu przerwania w pliku po stronie klienta może ulec następujące ograniczenia:  
  
-   Można ustawić punktów przerwania w ramach `<script>` bloków. Punkty przerwania w wbudowanego skryptu lub `<% %>` bloków nie może być mapowany.  
  
-   Adres URL przeglądarki dla strony musi zawierać nazwę strony. Na przykład http://microsoft.com/default.apsx. Mapowanie punktów przerwania nie może rozpoznać przekierowania z adresu, takich jak http://microsoft.com do domyślnej strony.  
  
-   Punkt przerwania musi być ustawiona na stronie określonego w adresie URL w przeglądarce, nie znajduje się w pliku sterowania (ascx) ASPX głównej strony lub innych plików uwzględnionych w tej strony. Nie można zamapować punktów przerwania ustawionych w dołączone stron.  
  
-   Ustawić punktów przerwania w `<script defer=true>` bloków nie może być mapowany.  
  
-   Aby ustawić punktów przerwania w `<script id="">` bloków, mapowanie punktów przerwania ignoruje `id` atrybutu.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapowanie punktów przerwania lub zduplikowane wiersze  
 Aby znaleźć odpowiedniej lokalizacji skryptu po stronie serwera i klienta, algorytm mapowanie punktu przerwania sprawdza, czy kod w każdym wierszu. Algorytm zakłada, że każdy wiersz jest unikatowy. Jeśli co najmniej dwa wiersze zawierają ten sam kod i ustaw punkt przerwania w jednym z tych zduplikowane wiersze, algorytm mapowanie punktu przerwania mogą wybrać niewłaściwy duplikat w pliku po stronie klienta. Aby temu zapobiec, Dodaj komentarz do wiersza, w którym został ustawiony punkt przerwania. Na przykład:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```