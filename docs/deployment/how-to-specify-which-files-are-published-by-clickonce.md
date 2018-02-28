---
title: "Porady: Określanie plików publikowanych za pomocą technologii ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: eee0e88b23a26ae7a89005ff304b565dd3d84c34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Porady: określanie plików publikowanych za pomocą technologii ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki aplikacji, wszystkie z systemem innym niż kodu w projekcie są wdrażane wraz z aplikacji. W niektórych przypadkach można mogą nie ma, należy opublikować określonych plików lub można zainstalować niektórych plików na podstawie warunków. Visual Studio oferuje możliwości Wyklucz pliki, pliki są oznaczane jako pliki danych lub wymagania wstępne i tworzenie grup plików instalacji warunkowego.  
  
 Pliki [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są zarządzane w **pliki aplikacji** okno dialogowe, dostępne z **publikowania** strony **projektanta projektu**.  
  
 Początkowo istnieje grupa pojedynczy plik o nazwie **(wymagane)**. Można tworzyć grup dodatkowych plików i przypisywać im plików. Nie można zmienić **grupy pobierania** plików, które są wymagane do uruchomienia aplikacji. Na przykład aplikacji .exe lub pliki oznaczone jako pliki danych, trzeba należeć do **(wymagane)** grupy.  
  
 Stan publikowania domyślne wartości pliku jest oznaczane **(automatycznie)**. Na przykład .exe aplikacji ma stan publikowania **Include (automatycznie)** domyślnie.  
  
 Pliki z **Akcja kompilacji** ustawioną właściwość **zawartości** są wyznaczone jako pliki aplikacji i zostanie oznaczony jako domyślnie włączone. One może być uwzględnione, wykluczone lub oznaczone jako pliki danych. Dostępne są następujące wyjątki:  
  
-   Pliki danych, takie jak pliki bazy danych SQL (*.mdf i .mdb) i pliki XML zostaną oznaczone jako pliki danych domyślnie.  
  
-   Podczas dodawania odwołania do odwołania do zestawów (pliki dll) są określone w następujący sposób: Jeśli **Kopiuj lokalnie** jest **False**, jest oznaczona domyślnie jako zestaw wymagań wstępnych (**(wymagań wstępnych Auto)**) który musi znajdować się w pamięci podręcznej GAC przed zainstalowaniem aplikacji. Jeśli **Kopiuj lokalnie** jest **True**, zestaw jest oznaczony jako domyślnie jako do zestawu aplikacji (**Include (automatycznie)**) i zostaną skopiowane do folderu aplikacji podczas instalacji. Odwołanie COM będą wyświetlane w **pliki aplikacji** okno dialogowe pola (jako pliku ocx) tylko wtedy, gdy jego **izolowany** właściwość jest ustawiona na **True**. Domyślnie zostanie on uwzględniony.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Aby dodać pliki do okna dialogowego plików aplikacji  
  
1.  Wybierz plik danych w **Eksploratora rozwiązań**.  
  
2.  W oknie Właściwości zmień **Akcja kompilacji** właściwości **zawartości** wartość.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Aby wykluczyć pliki z publikacji ClickOnce  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** oknie dialogowym Wybierz plik, który chcesz wykluczyć.  
  
5.  W **stan publikowania** pól, zaznacz **wykluczyć** z listy rozwijanej.  
  
### <a name="to-mark-files-as-data-files"></a>Aby oznaczyć pliki jako pliki danych  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** oknie dialogowym Wybierz plik, który chcesz oznaczyć jako dane.  
  
5.  W **stan publikowania** pól, zaznacz **pliku danych** z listy rozwijanej.  
  
### <a name="to-mark-files-as-prerequisites"></a>Aby oznaczyć pliki jako wstępnie wymagane składniki  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** oknie dialogowym Wybierz zestaw aplikacji (plik dll), którą chcesz oznaczyć jako warunek wstępny. Należy pamiętać, że aplikacja musi mieć odwołanie do zestawu aplikacji w celu znajdują się na liście.  
  
5.  W **stan publikowania** pól, zaznacz **wymagań wstępnych** z listy rozwijanej.  
  
### <a name="to-add-a-new-file-group"></a>Aby dodać nowe grupy plików  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** okno dialogowe, wybierz opcję **grupy** dla plików, które mają zostać uwzględnione w nowej grupie pole.  
  
    > [!NOTE]
    >  Pliki muszą mieć **Akcja kompilacji** ustawioną właściwość **zawartości** przed nazwy plików są wyświetlane w **pliki aplikacji** okno dialogowe.  
  
5.  W **grupy pobierania** pól, zaznacz  **\<nowy... >** z listy rozwijanej.  
  
6.  W **Nowa grupa** okno dialogowe, wprowadź nazwę grupy, a następnie kliknij przycisk **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Aby dodać plik do grupy  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** okno dialogowe, wybierz opcję **grupy** dla plików, które mają zostać uwzględnione w nowej grupie pole.  
  
5.  W **grupy pobierania** wybierz grupę z listy rozwijanej.  
  
    > [!NOTE]
    >  Nie można zmienić **grupy pobierania** plików, które są wymagane do uruchomienia aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)