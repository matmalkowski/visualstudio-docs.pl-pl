---
title: Tworzenie rozszerzenia z okna narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f918a5b8b48a7b9553cf3ca2e6c8fe9d38fbc9b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102151"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia z okna narzędzia
W tej procedurze zostanie przedstawiony sposób użyć szablonu projektu VSIX i **okna narzędzia niestandardowe** szablon elementu do utworzenia rozszerzenia z okna narzędzia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Utworzenie okna narzędzia  
  
1.  Tworzenie projektu VSIX o nazwie **FirstWindow**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Po otwarciu projektu dodać szablon elementu okna narzędzia o nazwie **MyWindow**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **okna narzędzia niestandardowe**. W **nazwa** u dołu okna, Zmień nazwę pliku okna narzędzia, aby **MyWindow.cs**.  
  
3.  Skompiluj projekt i Rozpocznij debugowanie.  
  
     Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat eksperymentalne wystąpienie, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).  
  
4.  W eksperymentalnym wystąpieniu, przejdź do **widoku / inne okna**.  
  
     Powinien zostać wyświetlony element menu dla **MyWindow**. Kliknij go.  
  
     Powinny pojawić się okno z tytułem **MyWindow** i informacją o tym przycisku **kliknij mnie!.**