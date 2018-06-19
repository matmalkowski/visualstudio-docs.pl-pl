---
title: Podstawowe informacje dotyczące integracji kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c3e93eb86fdc252f162331033207db5bdaa1569
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132037"
---
# <a name="source-control-integration-essentials"></a>Essentials integracji kontroli źródła
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa typy integracji kontroli źródła: wtyczka do kontroli źródła zapewnia podstawowe funkcje, który jest utworzony przy użyciu API dodatku typu Plug-in kontroli źródła (znanego wcześniej jako interfejs API MSSCCI) i rozwiązania integracji kontroli źródła na podstawie pakiet VSPackage który zapewnia bardziej niezawodne funkcje.  
  
## <a name="source-control-plug-in"></a>Wtyczka do kontroli źródła  
 Dodatek kontroli źródła są zapisywane jako bibliotekę DLL, która implementuje interfejs API dodatku typu Plug-in kontroli źródła. Funkcja integracji kontroli rejestracji i źródła jest zapewniana za pomocą interfejsu API. Ta metoda jest łatwiejsze do zaimplementowania niż kontroli źródła pakiet VSPackage i używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika (UI) dla większości operacji kontroli źródła.  
  
 Aby zaimplementować wtyczka do kontroli źródła przy użyciu interfejsu API dodatku typu Plug-in kontroli źródła, wykonaj następujące kroki:  
  
1.  Utwórz bibliotekę DLL, która implementuje funkcje wymienione w [kontroli źródła wtyczek](../../extensibility/source-control-plug-ins.md).  
  
2.  Zarejestruj plik DLL dokonując wpisy rejestru odpowiednich zgodnie z opisem w [porady: Instalowanie dodatku Plug-in kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Utwórz obiekt pomocnika interfejsu użytkownika i wyświetl ją po wyświetleniu monitu przez pakiet karty kontroli źródła ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składnik, który obsługuje funkcję kontroli źródła plug-in kontroli źródła).  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie Plug-in kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Pakiet VSPackage kontroli źródła  
 Kontroli źródła pakiet VSPackage implementacja pozwala na tworzenie dostosowanych zastępuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła formantu interfejsu użytkownika. Metoda ta umożliwia pełną kontrolę nad integracji kontroli źródła, ale użytkownik musi podać elementy interfejsu użytkownika i implementować interfejsów kontroli źródła, które będą udostępniane w ujęciu wtyczki.  
  
 Aby zaimplementować pakiet VSPackage kontroli źródła, należy:  
  
1.  Utwórz i Zarejestruj swoje własne kontroli źródła pakiet VSPackage, zgodnie z opisem w [rejestracji i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Zastąp kontroli źródła domyślnego interfejsu użytkownika niestandardowego interfejsu użytkownika. Zobacz [niestandardowego interfejsu użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Określ symbole do użycia i obsługi **Eksploratora rozwiązań** zdarzenia symbolu. Zobacz [kontrolki symbolu](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Obsługa zdarzeń zapytania, edytować i zapisywać zapytania, jak pokazano w [zapytania Edytuj Zapisz zapytanie](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie pakiet VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../../extensibility/internals/source-control-integration-overview.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)