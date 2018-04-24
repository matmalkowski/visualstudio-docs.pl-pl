---
title: 'Porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa0a4f458f264bdbdd1f96b414d0cc689bcfeb06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji
Po utworzeniu projektu w programie Visual Studio IDE, można przejrzeć informacje o tej kompilacji w **dane wyjściowe** okna. Za pomocą tych informacji, można na przykład rozwiązać niepowodzenie kompilacji. Dla projektów C++, można również wyświetlić te same informacje w *.txt* pliku, który został utworzony i zapisany automatycznie. Dla kodu zarządzanego projektów, można skopiować i wkleić informacje z **dane wyjściowe** okna do *.txt* plik i zapisać ją samodzielnie. Umożliwia także IDE do określenia, jakie informacje mają być wyświetlane o każdej kompilacji.  
  
 Jeśli dowolny rodzaj projektu tworzenia przy użyciu programu MSBuild, możesz utworzyć *.txt* pliku do zapisania informacji o kompilacji. Aby uzyskać więcej informacji, zobacz [Uzyskaj kompilacji dzienniki](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla projektów C++  
  
1.  W **Eksploratora Windows** lub **Eksploratora plików**, otwórz następujący plik:  *\\...\Visual Studio \<wersji\>\Projects\\ < ProjectName\>\\< ProjectName\>\Debug\\< ProjectName\>txt*  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu zarządzanego kodu  
  
1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
2.  W **dane wyjściowe** , korzystać z informacji z kompilacji, a następnie skopiuj go do **Schowka**.  
  
3.  Otwórz Edytor tekstu, takich jak **Notatnik**, Wklej informacje w pliku, a następnie zapisz go.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji znajdujących się w dzienniku kompilacji  
  
1.  Na pasku menu wybierz **narzędzia** > **opcje**.  
  
2.  Na **projekty i rozwiązania** wybierz pozycję **skompilować i uruchomić** strony.  
  
3.  W **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** listy, wybierz jedną z następujących wartości, a następnie wybierz **OK** przycisku.  
  
    |Poziom szczegółowości|Opis|  
    |---------------------|-----------------|  
    |**quiet**|Wyświetla podsumowanie tylko kompilacji.|  
    |**Minimalny**|Wyświetla podsumowanie kompilacji i błędy, ostrzeżenia i komunikaty, które są sklasyfikowane jako bardzo ważne.|  
    |**Normalny**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są sklasyfikowane jako ważne wysokiej; i głównych kroków kompilacji. Najczęściej użyjesz tego poziomu szczegółowości.|  
    |**Szczegółowy**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są sklasyfikowane jako ważne wysokiej; wszystkich kroków kompilacji; i komunikaty, które są podzielone na normalne znaczenie.|  
    |**Diagnostyka**|Wyświetla wszystkie dane, które jest dostępne dla kompilacji. Taki poziom szczegółowości można użyć do debugowania problemów ze skryptami niestandardowej kompilacji i inne problemy kompilacji.|  
  
     Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) i <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Należy ponownie zbudować projekt, aby zmiany zostały wprowadzone **dane wyjściowe** okna (wszystkich projektów) i  *<ProjectName>.txt* pliku (tylko dla projektów C++).  
  
## <a name="see-also"></a>Zobacz także  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Tworzenie i wyczyścić projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)