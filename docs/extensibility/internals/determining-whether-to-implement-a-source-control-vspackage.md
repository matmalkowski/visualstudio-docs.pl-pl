---
title: "Określanie, czy wdrożyć pakiet VSPackage kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 88281496c2e8350f910feda7934e2b55a494243b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Określanie, czy wdrożyć pakiet VSPackage kontroli źródła
W tej sekcji rosnącego wyborów plug-in kontroli źródła i kontroli źródła VSPackages do rozszerzania rozwiązania oraz zapewnia ogólnych wytycznych o wybieraniu ścieżki odpowiedniej integracji kontroli źródła.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Rozwiązanie kontroli źródła małych o ograniczonych zasobów  
 Jeśli ma ograniczone zasoby, a nie może być obciążać koszty zapisywania pakiet kontroli źródła, można utworzyć na podstawie interfejsu API dodatku typu Plug-in kontroli źródła wtyczek. Dzięki temu można działać równolegle z pakietów kontroli źródła, a można przełączać się między plug-in kontroli źródła i pakietów na żądanie. Aby uzyskać więcej informacji, zobacz [rejestracji i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Rozwiązanie kontroli źródła dużych z zestawem funkcji sformatowanego  
 Jeśli chcesz wdrożyć rozwiązanie kontroli źródła, które udostępnia model kontroli źródła sformatowanego, który nie jest odpowiednio przechwycone przy użyciu interfejsu API dodatku typu Plug-in kontroli źródła, można rozważyć jako ścieżka integracji pakiet kontroli źródła. Dotyczy to zwłaszcza, jeśli pakiet karty kontroli źródła, (która komunikuje się z Plug-in kontroli źródła oraz udostępnia podstawowe źródła formantu interfejsu użytkownika) zamiast spowodowałoby zastąpienie własnymi, dzięki czemu można obsługiwać zdarzenia kontroli źródła w niestandardowy sposób. Jeśli masz już zadowalające źródła kontroli interfejsu użytkownika i chcesz zachować środowiska w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], opcja pakietu kontroli źródła pozwala spełniają właśnie tę funkcję. Pakiet kontroli źródła nie jest rodzajowa i jest przeznaczona wyłącznie do użytku z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Jeśli chcesz wdrożyć rozwiązanie do kontroli źródła, które zapewnia elastyczność i bardziej zaawansowane funkcje kontroli nad logikę kontroli źródła i interfejsu użytkownika, możesz trasy integracji pakietu kontroli źródła. Można:  
  
1.  Zarejestruj swoje własne pakiet VSPackage kontroli źródła (zobacz [rejestracji i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Zamień kontroli źródła domyślnego interfejsu użytkownika niestandardowego interfejsu użytkownika (zobacz [niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Określ symbole, można użyć do obsługi zdarzeń symbolu w Eksploratorze rozwiązań (zobacz [kontrolki symbolu](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Obsługa zdarzeń zapytania, edytować i zapisywać zapytania (zobacz [zapytania Edytuj Zapisz zapytanie](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)