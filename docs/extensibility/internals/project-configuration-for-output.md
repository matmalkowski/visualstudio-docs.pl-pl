---
title: "Konfiguracja dla danych wyjściowych projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>Konfiguracja projektu dla danych wyjściowych
Co konfiguracja może obsługiwać zestaw procesów kompilacji, które wywołują elementów wyjściowych, takich jak pliki wykonywalne lub zasobu. Te elementy dane wyjściowe są prywatne dla użytkownika i można umieścić w grupach, które łącze powiązanych typów danych wyjściowych, takich jak pliki wykonywalne (.exe, dll, .lib) i pliki źródłowe (.idl, pliki .h).  
  
 Elementy danych wyjściowych może zostać udostępniona za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod i wyliczenia z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metody. Jeśli chcesz grupować elementy danych wyjściowych projektu powinny również implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfejsu.  
  
 Konstrukcja opracowany zaimplementowanie `IVsOutputGroup` umożliwia projekty do wyjścia grupy zgodnie z użycia. Na przykład biblioteki DLL może być zgrupowane z jej bazą danych programu (PDB).  
  
> [!NOTE]
>  Plik PDB zawiera informacje o debugowaniu i jest tworzona, jeśli określono opcję "Generuj informacje debugowania" podczas kompilowania .dll lub .exe. Plik PDB jest zwykle generowane dla debugowania projektu tylko konfiguracji.  
  
 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji, który ją obsługuje, nawet jeśli liczba wyjść zawarty w grupie może się różnić od konfiguracja. Na przykład projektu Matt biblioteki DLL może uwzględniać mattd.dll i mattd.pdb w konfiguracji debugowania, ale tylko obejmują matt.dll w sprzedaży detalicznej konfiguracji.  
  
 Grupy również mają te same informacje identyfikator, takie jak nazwa kanoniczna, nazwa wyświetlana i informacje o grupie, konfiguracja konfiguracja w projekcie. Ta spójności umożliwia wdrażanie i opakowanie w dalszym ciągu działać nawet w przypadku zmiany konfiguracji.  
  
 Grupy mogą być również klucza danych wyjściowych, umożliwiający pakowania skróty do punktu, wpisując tekst opisowy. Wszystkie grupy może być pusty w danej konfiguracji, dlatego należy wprowadzać żadnych założeń o rozmiarze grupy. Rozmiar (liczba wyjść) każdej grupy w żadnej konfiguracji może być inny niż rozmiar innej grupy w tej samej konfiguracji. Może być również inny niż rozmiar tej samej grupy w innej konfiguracji.  
  
 ![Grafika przedstawiająca grupy danych wyjściowych](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupy danych wyjściowych  
  
 Podstawowym zastosowaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfejsu jest zapewnienie dostępu do tworzenia, wdrażania i debugowania obiektów zarządzania i Zezwalaj projektów swobody grupy danych wyjściowych. Aby uzyskać więcej informacji na użycie tego interfejsu, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md).  
  
 Poprzedni diagram grupy wbudowane ma klucz, więc dane wyjściowe w konfiguracji (bD.exe lub b.exe) użytkownik może utworzyć skrót do wbudowane i dowiedzieć się, że skrót będzie działać niezależnie od konfiguracji wdrożonego. Grupy źródło nie ma klucza output, więc użytkownik nie można utworzyć skrótu do niego. Jeśli debugowanie grupy wbudowane ma kluczowe dane wyjściowe, ale wbudowane grupy detalicznej nie, który może być niepoprawna implementacja. Dlatego, następnie, jeśli grupy, która zawiera dane wyjściowe nie ma żadnej konfiguracji i w związku z tym nie plik klucza, a następnie inne konfiguracje z tej grupy, które zawierają dane wyjściowe nie może mieć pliki klucza. Edytory Instalator założono, że nazwy kanonicznej i wyświetlane nazwy grup, a także istnienie plik klucza nie należy zmieniać w konfiguracji.  
  
 Należy pamiętać, że jeśli projekt ma `IVsOutputGroup` czy nie ma do pakietu lub wdrożenia, wystarczy nie można umieścić te dane wyjściowe w grupie. Dane wyjściowe mogą być wyliczane nadal normalnie zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodę, która zwraca wszystkie dane wyjściowe konfiguracji niezależnie od grupowania.  
  
 Aby uzyskać więcej informacji, zobacz wykonania `IVsOutputGroup` w przykładowym niestandardowe projektu w [MPF projektów](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)