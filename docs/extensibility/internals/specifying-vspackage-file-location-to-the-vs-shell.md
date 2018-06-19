---
title: Określanie lokalizacji pliku pakiet VSPackage powłoki programu VS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a4270fbd723e6c5aa6f16066066e0ca4ac74e5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132005"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Określanie lokalizacji pliku pakiet VSPackage powłoki programu VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi mieć możliwość zlokalizować zestawu DLL załadować pakiet VSPackage. Można znaleźć go na różne sposoby, zgodnie z opisem w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|Użyj klucza rejestru CodeBase.|Klucz CodeBase może służyć do kierowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można załadować zestawu pakiet VSPackage z dowolną pliku w pełni kwalifikowaną ścieżkę. Wartość klucza powinien być ścieżka do pliku DLL. Jest to najlepszy sposób, aby mieć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadować zestawu z pakietu. Ta metoda jest czasami określane jako "CodeBase/private instalacji directory technika." Podczas rejestracji wartość codebase jest przekazywana do klas atrybutów rejestracji wystąpienia <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> typu.|  
|Umieść biblioteki DLL do **PrivateAssemblies** katalogu.|Umieść zestawu w **PrivateAssemblies** podkatalog [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] katalogu. Zestawy znajduje się w **PrivateAssemblies** są wykrywane automatycznie, ale nie są widoczne w **Dodaj odwołania** okno dialogowe. Różnica między **PrivateAssemblies** i **PublicAssemblies** jest to, że zestawy w **PublicAssemblies** znajduje się w **Dodaj odwołania**  okno dialogowe. Jeśli wybrano opcję Użyj techniki "katalog instalacyjny prywatnych/CodeBase", a następnie należy zainstalować w **PrivateAssemblies** katalogu.|  
|Użyj zestawu z silną nazwą i zestawu klucza rejestru.|Klucz zestawu może służyć do kierowania jawnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadować silne o nazwie zestawu pakiet VSPackage. Wartość klucza należy silnej nazwy zestawu.|  
|Umieść biblioteki DLL do **PublicAssemblies** katalogu.|Na koniec zestawu mogą również być umieszczane w **PublicAssemblies** podkatalogu. Zestawy znajduje się w **PublicAssemblies** są wykrywane automatycznie, a także będą wyświetlane w **Dodaj odwołania** okno dialogowe w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Zestawy pakiet VSPackage można umieścić wyłącznie w **PublicAssemblies** katalogu, jeśli zawierają one zarządzane składniki, które mają być ponownie używane przez innych pakiet VSPackage. Większość zestawów nie spełnia tego kryterium.|  
  
> [!NOTE]
>  Zestawy o silnych nazwach, podpisem używać dla wszystkich sieci zestawów zależnych. Te zestawy należy również zainstalować w własnego katalogu lub globalnej pamięci podręcznej zestawów (GAC). Chroni to przed powoduje konflikt z zestawów, które mają taką samą nazwę pliku podstawowego, znany jako powiązania nazwy niska.