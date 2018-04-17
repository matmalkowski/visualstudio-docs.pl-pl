---
title: Dostęp do buforu tekstu przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84bf79ea19fc0867643ce3e8ee6db0a645d9a0dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Dostęp do buforu tekstu przy użyciu interfejsu API starsza wersja
Tekst jest odpowiedzialny za zarządzanie strumienie tekstu i plik trwałości. Mimo że buforu można odczytu lub zapisu w innych formatach, cała komunikacja zwykłej z buforu odbywa się przy użyciu Unicode. W starszych interfejsów API bufor tekstowy umożliwia jedno - albo dwuwymiarowa współrzędnych identyfikują lokalizacje znak w buforze.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Wymiar jednego i dwa koordynacji systemów  
 Jednowymiarowa pozycji współrzędnych opiera się na pozycji znaku od pierwszego znaku w buforze, takich jak 147. Możesz użyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfejsu dostęp do jednowymiarowego lokalizacji w buforze. Dwuwymiarowa współrzędnych opiera się na pary wiersza oraz indeksu. Na przykład znak w buforze na 43 5 będzie w wierszu 43, pięć znaków z prawej strony pierwszy znak w tym wierszu. Dostęp dwuwymiarowa lokalizację w buforze przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsu. Zarówno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfejsów implementowanych przez obiekt buforu tekstu (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) i jest dostępny od siebie przy użyciu `QueryInterface`. Na poniższym diagramie przedstawiono te i inne interfejsy klucza na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Text Buffer Object](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Obiekt buforu tekstu  
  
 Chociaż albo współrzędnych działa w buforze tekstu, jest zoptymalizowany do użycia dwuwymiarowe współrzędne. Jednowymiarowa współrzędnych można utworzyć zmniejszenie wydajności. Dlatego należy używać dwuwymiarowa układ współrzędnych, jeśli to możliwe.  
  
 Tekst drugiego odpowiedzialność buforu jest trwałości pliku. Aby to zrobić, obiekt buforu tekstu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i działa jako składnik obiektu danych dokumentu dla elementów projektu i innych składników środowiska objętego trwałości. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zmiana ustawień widoku przy użyciu interfejsu API starsza wersja](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Wyjaśniono, jak zmienić ustawienia widoku przy użyciu starszej wersji interfejsu API.  
  
 [Za pomocą Menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Wyjaśniono, jak monitorować ustawienia globalne za pomocą Menedżera tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze Core](../extensibility/inside-the-core-editor.md)