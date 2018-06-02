---
title: Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47a519db245e2ec15548ba1d46a583d0a73f466f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693487"
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji
  W programie Visual Studio można utworzyć niestandardowe kontrolki do ponownego użycia, które mogą być używane przez stron aplikacji i składników Web Part, które są uruchamiane w programie SharePoint. Formanty te są nazywane kontrolki użytkownika. Kontrola użytkownika to rodzaj typu złożonego formantu, który działa podobnie jak strony sieci Web platformy ASP.NET — Dodawanie istniejącego kontrolki serwera sieci Web i znaczników do formantu użytkownika i definiowanie właściwości i metody dla formantu. Następnie można osadzać na stronach sieci Web ASP.NET, w którym działają jako jednostka.  
  
## <a name="create-a-user-control"></a>Tworzenie formantu użytkownika
 Aby utworzyć kontrolkę użytkownika, należy dodać **kontrolki użytkownika** do **pusty projekt SharePoint**. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie formantu użytkownika dla strony aplikacji SharePoint lub składnik Web Part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Po dodaniu **kontrolki użytkownika** elementu, Visual Studio tworzy folder w projekcie, a następnie dodaje kilka plików do folderu. W poniższej tabeli opisano każdego pliku.  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik kontrolki użytkownika|Określa formant użytkownika. Projektowanie kontrolki użytkownika przez dodanie formanty i kod znaczników do tego pliku.|  
|Plik kodu|Zawiera kod związany z kontrolki użytkownika. Dodaj kod obsługi zdarzenia do tego pliku.|  
|Kod projektanta pliku|Zawiera kod wygenerowany przez projektanta i nie powinny być edytowane bezpośrednio.|  
  
## <a name="design-the-user-control"></a>Projekt kontrolki użytkownika
 Projektowanie kontrolki użytkownika przy użyciu narzędzia Projektant Visual Web Developer w programie Visual Studio. Ten Projektant pojawia się po otwarciu pliku kontrolki użytkownika w projekcie i wybierz **projekt** kartę.  

## <a name="consume-the-user-control"></a>Używać formantu użytkownika
 Formanty użytkownika są wyświetlane w programie SharePoint dopiero dołączać do strony aplikacji lub składnika Web Part.  
  
 Aby uwzględnić kontrolki użytkownika na stronie aplikacji, otwórz strony sieci Web, do której chcesz dodać kontrolkę użytkownika platformy ASP.NET. Przełącz do widoku projektu, a następnie wybierz pliku kontrolki użytkownika niestandardowego w Eksploratorze rozwiązań i przeciągnij go na stronie. Formant użytkownika ASP.NET został dodany do strony i Projektant tworzy dyrektywy @ rejestru, który jest wymagany dla strony, aby rozpoznać kontrolki użytkownika. Teraz możesz pracować z publicznej właściwości i metod formantu.  
  
 Aby uwzględnić kontrolkę użytkownika w części sieci Web, Dodaj kontrolkę użytkownika do składnika Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekcji w pliku kodu składnika Web Part. Poniższy przykład umożliwia dodanie formantu użytkownika <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekcji części sieci Web.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Debugowanie kontrolki użytkownika
 Aby debugować kontrolki użytkownika, upewnij się, że formant użytkownika znajduje się na stronie aplikacji lub składnika Web Part w projekcie programu SharePoint. Następnie można debugowania kodu w formancie użytkownika, tak jak będzie debugowania kodu w dowolnym projektu programu Visual Studio.  
  
 Po uruchomieniu debugera programu Visual Studio Visual Studio otworzy w witrynie programu SharePoint.  
  
 W programie SharePoint otwórz stronę aplikacji, która zawiera kontrolki użytkownika. Jeśli formant użytkownika znajduje się w części sieci Web, należy dodać składnik Web Part do strony składnika Web Part programu SharePoint.  
  
 Aby uzyskać więcej informacji o debugowaniu projektów SharePoint, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie kontrolki użytkownika dla części sieciowej lub strony aplikacji SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Pokazuje, jak utworzyć niestandardowe kontrolki do ponownego użycia, które mogą być używane przez stron aplikacji i składników Web Part, które są uruchamiane w programie SharePoint.|  
  