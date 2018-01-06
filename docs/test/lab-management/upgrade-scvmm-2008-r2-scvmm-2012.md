---
title: Uaktualnienie programu SCVMM 2008 R2 do programu SCVMM 2012 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7a50c075effd8c1bb63bd56b7fab04a7509d23e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Uaktualnienie programu SCVMM 2008 R2 do programu SCVMM 2012

Lab Management programu Team Foundation Server obsługuje SCVMM 2008 R2 i programu SCVMM 2012. Jeśli uaktualniania do wersji Team Foundation Server 2015 Team Foundation Server 2013, a następnie zaplanować uaktualnienie programu SCVMM 2008 R2 do programu SCVMM 2012, zaleca się uaktualnienie do programu SCVMM 2012 po wykonaniu uaktualnienia do programu Team Foundation Server 2015. W tym temacie opisano sposób uaktualniania programu SCVMM 2008 R2 do programu SCVMM 2012, gdy używasz Lab Management na Team Foundation Server 2015.
Lab Management **nie** obsługi w programie SCVMM 2016. 

**Ważne:** po uaktualnieniu programu SCVMM pewnych dodatkowych kroków spowoduje, że przestój dla serwera Team Foundation Server. Zawiera ona następujące kroki.

## <a name="upgrading-to-scvmm-2012"></a>Uaktualnianie do programu SCVMM 2012

1. Uaktualnienie serwera programu SCVMM 2008 R2 do programu SCVMM 2012 serwer przy użyciu Instalatora programu SCVMM 2012.

1. Uaktualnij agentów programu SCVMM na hostach i udziały biblioteki.

1. Użyj konsoli administracyjnej programu SCVMM, aby sprawdzić, czy działają wszystkie składniki programu SCVMM.

1. Zainstaluj konsolę administracyjną programu SCVMM 2012 na wszystkich maszynach warstwy aplikacji serwera Team Foundation Server.

1. Użyj **iisreset** polecenie, aby ponownie uruchomić usługę sieci web serwera Team Foundation Server. Następnie uruchom ponownie agenta zadania serwera Team Foundation Server.

   **Uwaga:** ten krok spowoduje to zakłócenia usługi na Team Foundation Server.

1. Uaktualnienie danych i szablonów w każdej bazie danych kolekcji projektów, nie jest zgodna z programu SCVMM 
   2012.

   Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na serwerze Team Foundation Server, a następnie wprowadź następujące polecenie:

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\narzędzia\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Jeśli używasz **upgradeSCVMM** polecenia Team Foundation Server spowoduje utworzenie nowego obiektu szablonu na serwer SCVMM dla każdego projektu zespołowego, który korzysta z tego szablonu. Dzięki temu uaktualnienia szablonów w celu zachowania zgodności z programu SCVMM 2012 bez utraty danych. Podczas tworzenia nowych szablonów, nazwę projektu zespołowego jest dołączany do nazwy szablonu.

   **Uwaga:**  
   Jeśli nowa nazwa szablonu jest większa niż 64 znaki, spowoduje to niepowodzenie programu SCVMM. Aby rozwiązać ten problem, Podaj krótszą nazwę tych szablonów. Jeśli wystąpiły jakiekolwiek błędy i ostrzeżenia podczas uruchamiania tego polecenia, zobacz następną sekcję, aby usunąć te błędy. Jeśli nie wystąpiły jakiekolwiek błędy i ostrzeżenia, zakończeniu uaktualniania, a następnie można rozpocząć używanie środowiska SCVMM z Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Rozwiązywanie błędów i ostrzeżeń, korzystając z polecenia upgradeSCVMM

Po użyciu **upgradeSCVMM** polecenia, należy rozwiązać wszystkie błędy lub ostrzeżenia możesz otrzymywać, a następnie ponownie uruchom polecenie, aby umożliwić korzystanie ze środowiska laboratoryjnego. **UpgradeSCVMM** polecenie generuje plik dziennika, który zawiera informacje o wszelkie błędy i ostrzeżenia, które wystąpią. Lokalizacja pliku dziennika jest wyświetlany po uruchomieniu **upgradeSCVMM** polecenia.

**Błąd programu SCVMM:** Jeśli zostanie wyświetlony błąd jest związany z błędem SCVMM, użyj historię zadania SCVMM, aby uzyskać dodatkowe informacje o tym błędzie. Uruchom ponownie po rozwiązaniu błąd w programie SCVMM, **upgradeSCVMM** polecenia.

## <a name="see-also"></a>Zobacz także

* [Zmiana istniejących konfiguracji programu Lab Management](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
