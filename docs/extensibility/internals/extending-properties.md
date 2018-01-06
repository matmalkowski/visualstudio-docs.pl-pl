---
title: "Rozszerzanie właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c47295c1906c6517638bdf8e9c3a55897f38aa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-properties"></a>Rozszerzanie właściwości
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Właściwości** okna jest przeglądarką uniwersalnych właściwości dla składników COM i COM + i obsługuje wszystkie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produktów. **Właściwości** okna współpracuje z `ITypeInfo` wpisz informacje i metadanych modelu COM +, aby wyświetlić właściwości czasu projektowania dla aktualnie wybranego obiektu w innym oknie zintegrowane środowisko programistyczne (IDE).  
  
 **Właściwości** okna, które mogą być otwierane przez naciśnięcie przycisku F4 na klawiaturze lub wybierając **okna właściwości** na **widoku** menu służy do wyświetlania i edytowania niezależne od konfiguracji, w czasie projektowania właściwości i zdarzenia wybranych obiektów. Właściwości zależne od konfiguracji, skojarzone z rozwiązań i projektów, są wyświetlane na [strony właściwości](../../extensibility/internals/property-pages.md). Aby uzyskać więcej informacji, zobacz [właściwości NIB: projekt](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md), i [zarządzania NIB: element w projektach](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Przegląd okna właściwości](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Okno właściwości  
  
 Ta sekcja zawiera szczegółowe informacje, które odnoszą się do poszczególnych obszarach **właściwości** okna i interfejsów, które należy zaimplementować i wywołania do wypełnienia okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie okna właściwości](../../extensibility/internals/properties-window-overview.md)  
 Objaśnienie jego przeznaczenia **właściwości** okna względem okna narzędzia i okna dokumentu.  
  
 [Szablon zasad i okno właściwości](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Omówiono sposób projektu znajduje się w szablonie projektu w przedsiębiorstwie oraz jak szablonu projektu przedsiębiorstwa mogą wymusić zasady.  
  
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Wyjaśniono podstawę do wyboru, która określa, jakie informacje są wyświetlane w **właściwości** okna.  
  
 [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md)  
 Opisuje cel **właściwości** okno Lista obiektów, opisujące, jak to zrobić, podczas różne obiekty z tej listy wyzwala wywołanie, środowisko zostanie poinformowany, czy został on wybrany nowy obiekt.  
  
 [Przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md)  
 Objaśnienie jego przeznaczenia cztery domyślne przyciski wyświetlane na **właściwości** pasek narzędzi okna.  
  
 [Siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md)  
 Wyjaśnia, gdzie znaleziono nazw właściwości i pola wartości właściwości w siatce.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono projektów jako bloków konstrukcyjnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)  
 W tym artykule opisano, jak używasz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platformy stale testowanie i debugowanie aplikacji podczas ich tworzenia.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 W tym artykule opisano `IDispatch` interfejs, który najpierw została zaprojektowana do obsługi automatyzacji, podając mechanizm późnym wiązaniem dostępu i pobieranie informacji na temat metody i właściwości obiektu.  
  
 [Zarządzanie ustawieniami aplikacji (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Omówienie ustawień aplikacji, które pozwalają skonfigurować aplikację tak, aby wartości właściwości są przechowywane w pliku konfiguracyjnym zewnętrznych zamiast skompilowanego kodu aplikacji.  
  
 [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Wyjaśniono, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wydajnie zarządza elementy, takie jak odwołania, połączeń danych, folderów i plików, które są wymagane przez użytkownika nakład pracy za pośrednictwem rozwiązania i projekty.  
  
 [Rozszerzanie innych części programu Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśniono, jak używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usługi w celu utworzenia elementów interfejsu użytkownika, zgodne z resztą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].