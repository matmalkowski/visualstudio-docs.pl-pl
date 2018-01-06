---
title: "Metadane jako źródło | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 29b783e20925b3eaa4a7b0956fdcfdbcab06a328
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-as-source"></a>Metadane jako źródło
Metadane jako źródło umożliwia wyświetlenie metadanych, który jest wyświetlany jako kodu źródłowego C# w buforze tylko do odczytu. Dzięki temu widok deklaracje typów i członków (bez implementacji). Metadane jako źródło można wyświetlić, uruchamiając **przejdź do definicji** polecenia dla typów albo elementów członkowskich, których kod źródłowy nie jest dostępny w projekcie lub rozwiązaniu.  
  
> [!NOTE]
>  Podczas próby uruchomienia **przejdź do definicji** polecenia dla typów albo elementów członkowskich, które są oznaczone jako wewnętrzne, zintegrowane środowisko programistyczne (IDE) nie są wyświetlane ich metadanych jako źródła, niezależnie od tego, czy odwołaniem do zestawu jest znajomym, czy nie.  
  
 Można wyświetlić metadane jako źródło w obu edytora kodu lub **definicji kodu** okna.  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Podgląd metadanych jako źródła w edytorze kodu  
 Po uruchomieniu **przejdź do definicji** polecenia dla elementu, którego kod źródłowy jest niedostępny, dokument z kartami zawiera widok metadanych tego elementu wyświetlana jako źródła, zostanie wyświetlony w edytorze kodu. Nazwa typu, a następnie **[z metadanych]**, zostanie wyświetlony na karcie dokumentu.  
  
 Na przykład, jeśli uruchomisz **przejdź do definicji** polecenia dla <xref:System.Console>, metadane <xref:System.Console> zostanie wyświetlony w edytorze kodu jako kod źródłowy C# podobny jego deklaracji, ale bez implementacji.  
  
 ![Metadane jako źródło](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Podgląd metadanych jako źródła w okno definicji kodu  
 Gdy **definicji kodu** okno jest aktywne lub widoczne, IDE automatycznie wykonuje **przejdź do definicji** polecenia dla elementów w obszarze kursora w edytorze kodu i dla elementów, które są wybrane w  **Widok klasy** lub **przeglądarka obiektów**. Jeśli kod źródłowy jest niedostępny dla tego elementu, IDE będzie wyświetlany jako źródło w metadanych elementu **definicji kodu** okna.  
  
 Na przykład, jeśli umieść kursor w wyrazie <xref:System.Console> w edytorze kodu, metadane <xref:System.Console> pojawia się jako źródło w **definicji kodu** okna. Podobny źródło <xref:System.Console> deklaracji, ale bez implementacji.  
  
 Jeśli chcesz wyświetlić deklaracji elementu, który jest wyświetlany w **definicji kodu** okna, kliknij prawym przyciskiem myszy element i kliknij przycisk **przejdź do definicji**.