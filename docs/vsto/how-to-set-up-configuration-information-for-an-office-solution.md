---
title: "Porady: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f604fa40a9816d5e46593bc50fcb91f82d13325
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Porady: ustawianie informacji o konfiguracji dla rozwiązań pakietu Office
  Pliki konfiguracji można użyć do konfigurowania ustawień, które są specyficzne dla rozwiązań pakietu Office. Można określić ustawienia, takie jak zasady powiązanie zestawu, obiektów zdalnych, debugowania i ustawień śledzenia.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Aby dodać plik konfiguracji do projektu pakietu Office  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **kategorii** okienku, kliknij przycisk **ogólne**.  
  
3.  W **szablony** okienku wybierz **pliku konfiguracji aplikacji**.  
  
4.  W **nazwa** wpisz taką samą nazwę jako zestaw plus .config rozszerzenia. Na przykład plik konfiguracji dla programu Excel zestawu projektu o nazwie ExcelWorkbook1.dll będzie nosić ExcelWorkbook1.dll.config.  
  
5.  Kliknij przycisk **Dodaj**.  
  
6.  Utwórz plik konfiguracji schemat pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [schemat pliku konfiguracji dla programu .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Nie istnieją żadne uwagi dotyczące z projektów pakietu Office za pomocą plików konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji dla programu .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  