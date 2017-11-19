---
title: "Rozszerzanie i dostosowywanie narzędzi systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6488df3ec567051709f6464d49d891cdd8f995dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-and-customizing-tool-windows"></a>Rozszerzanie i dostosowywanie narzędzi systemu Windows
Program Visual Studio udostępnia wiele różnych typów systemu windows, na przykład okna narzędzi okna dokumentów i okno dialogowe systemu windows. Inne okna, takie jak okna właściwości, w oknie danych wyjściowych i w oknie Lista zadań, są typy okien narzędzi.  
  
## <a name="tool-windows"></a>Okna narzędzi  
 Visual Studio narzędzia windows są zwykle tylko do odczytu systemu windows, które nie są oparte na pliku. W tym różnią się one z okna dokumentów, które zawierają pliki w trybie odczytu i zapisu. **Przybornika**, **Eksploratora rozwiązań**, **właściwości** okno i **przeglądarki sieci Web** przedstawiono okna narzędzi.  
  
 Aby dowiedzieć się, jak można utworzyć okna proste narzędzie, zobacz [Dodawanie okna narzędzia](../extensibility/adding-a-tool-window.md).  
  
 Aby zarejestrować okna narzędzia z programem Visual Studio, zobacz [rejestrowanie okna narzędzia](../extensibility/registering-a-tool-window.md).  
  
 Okna narzędzi jest pojedynczym wystąpieniem domyślnym, co oznacza, że tylko jedno wystąpienie okna narzędzia może być otwarty naraz. Po otwarciu okna narzędzia jednego wystąpienia pozostaje otwarty do czasu zamknięcia IDE. Po zamknięciu okna narzędzia jednym wystąpieniu, jego zmiany widoczności. Można również utworzyć wiele wystąpień narzędzia windows tak, aby wiele wystąpień okna mogą być otwarte jednocześnie. Zobacz [tworzenia okna narzędzia wielu wystąpieniach](../extensibility/creating-a-multi-instance-tool-window.md) Aby uzyskać więcej informacji.  
  
 Narzędzia systemu windows może być *dynamiczne*, co oznacza, że są one widoczne zawsze, gdy dotyczy ich powiązane kontekście interfejsu użytkownika. Używanie widoczności automatycznego można zmniejszyć niepotrzebnych danych systemu windows w środowisku IDE. Aby uzyskać więcej informacji, zobacz [otwierania dynamiczne okna narzędzia](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Narzędzia systemu windows może być zadokowane, zmiennoprzecinkowych lub kartach w ramce dokumentu. Ramki okna narzędzi jest zapewniana przez IDE i służy do kontrolowania rozmiaru, lokalizacji, stanu dokowania i inne właściwości trwałych. W okienku okna narzędzia Wyświetla zawartość. Domyślny rozmiar i położenie zastosowanie, tylko gdy okno narzędzia pierwszym otwarciu; Po utworzeniu tego stanu okna narzędzia jest trwały.  
  
 Okienka narzędzi można udostępniać formanty użytkownika WPF i obsługuje paski narzędzi. Można zastąpić <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> właściwości do zwrócenia uchwytu obsługiwanego formantu.  
  
 Narzędzia systemu Windows można dodać wiele różnych funkcji. Na przykład można dodać paska narzędzi: [Dodawanie paska narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: [Dodawanie Menu skrótów okna narzędzia](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać formantu wyszukiwania, który służy do wyszukiwania elementów wewnątrz okna narzędzia: [Dodawanie wyszukiwania do okna narzędzia](../extensibility/adding-search-to-a-tool-window.md).  
  
 Będzie możliwe subskrybowanie zdarzeń okna narzędzia: [subskrybowanie zdarzeń](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Rozszerzanie istniejących okna narzędzi  
 Można dodać informacji o okna narzędzia na nowy **opcje** strony i nowe ustawienie na **właściwości** pozycję zapisu **listy zadań** i **danych wyjściowych**  systemu windows. Aby uzyskać więcej informacji, zobacz [właściwości, lista zadań, danych wyjściowych i opcje Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) i [właściwości, lista zadań, danych wyjściowych i opcje Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe  
 Rozszerzenia programu Visual Studio należy utworzyć modalnych okien dialogowych za wyprowadzanie je z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, co pozwala na kontrolowanie je i pozostałej części interfejsu użytkownika. Aby uzyskać więcej informacji zobacz. [Tworzenie i zarządzanie nimi modalnych okien dialogowych](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md)