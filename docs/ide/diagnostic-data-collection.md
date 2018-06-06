---
title: Dzienniki generowane przez system i danych diagnostycznych
ms.date: 05/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: michma
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f55d8a0f32886ed477026e298ed2c8c5d6e26f16
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34478349"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Dzienniki generowane przez system zebrane przez program Visual Studio

Visual Studio zbiera dzienniki generowanych przez system do rozwiązywania problemów oraz do poprawy jakości produktu za pomocą [Program poprawy jakości obsługi klienta programu Visual Studio](visual-studio-experience-improvement-program.md). Ten artykuł zawiera niektóre informacje na temat typów danych, które zbieramy, i jak możemy użyć. Umożliwia także wskazówki dotyczące sposobu rozszerzenia autorów można uniknąć lub przypadkowego ujawnienia informacji osobistych lub poufnych.

## <a name="types-of-collected-data"></a>Typy zebranych danych

Visual Studio zbiera dzienniki awarii (Crash), zawiesza się, brak reakcji interfejsu użytkownika i wysokiego użycia procesora CPU lub pamięci generowanych przez system. Możemy również zbierać informacji na temat błędów występujących podczas instalacji produktu lub użycia. Zebrane dane w zależności od błędu i mogą zawierać ślady stosu, zrzuty pamięci i informacje o wyjątku:

- Wysokie użycie procesora CPU i braku odpowiedzi są zbierane śladów stosu odpowiednich wątków programu Visual Studio.

- Przypadki, w którym śladów stosu niektórych wątków nie są wystarczająco dużo, aby określić katalog główny przyczyną tego problemu, na przykład awarii (Crash), zawiesza się lub wysokie użycie pamięci, jakie zbieramy pamięci *zrzutu*. Zrzut reprezentuje stan procesu, gdy wystąpił błąd.

- Wystąpił nieoczekiwany błąd warunki, na przykład wystąpił wyjątek podczas próby zapisu do pliku na dysku, zbierane są informacje o wyjątku. Informacje obejmują nazwę wyjątku, ślad stosu wątku, w którym wystąpił wyjątek, komunikat skojarzony z wyjątkiem i inne informacje potrzebne do określonego wyjątku.

   Poniższy przykład przedstawia zebrane dane przedstawia nazwa wyjątku, ślad stosu i komunikat o wyjątku:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Wykorzystanie dzienników generowanych przez system

Przepływ pracy, aby ustalić przyczynę błędu zależy od typu błędu i jego ważności.

### <a name="error-classification"></a>Błąd klasyfikacji

Oparty na dziennikach, błędy są sklasyfikowane i zliczane priorytety dochodzenia. Na przykład firma Microsoft może stwierdzić, że "System.IO. \__Error.WinIOError "na"System.IO.FileStream.Init"Wystąpił 500 razy w wersji \<x > produktu, i ma najwyższy stopień wystąpienie w tej wersji.

### <a name="work-items-for-tracking"></a>Elementy pracy dla śledzenia

Elementy pracy dla poszczególnych, priorytetową błędy są tworzone i przypisane do engineers, aby umożliwić zbadanie problemu. Te elementy robocze zawierają zwykle klasyfikacji, priorytet i informacje diagnostyczne dotyczące typu błędu. Te informacje jest pochodną zebranych dzienników generowanych przez system tego błędu. Na przykład elementu pracy dla awarii może zawierać ślad stosu, gdzie występuje awaria.

### <a name="error-investigation"></a>Błąd podczas badania

Inżynierów użyć informacji dostępnych w elementu roboczego do ustalenia głównej przyczyny błędu. W niektórych przypadkach potrzebuje więcej informacji, niż jest to w element roboczy w takim przypadku odnoszą się do oryginalnej dziennika generowanych przez system, który został zebrany. Na przykład inżyniera może sprawdzić zrzutu pamięci, aby zrozumieć awarii produktu.

## <a name="tips-for-extension-authors"></a>Porady dotyczące autorów rozszerzenia

Autorzy rozszerzenia należy ograniczyć ujawnienia informacji osobistych, które nie są używane osobistych lub inne poufne informacje w nazwach modułów, typy i metody. W przypadku awarii lub podobne błąd z kodem na stosie, te informacje pobiera zbierane w ramach dzienników generowanych przez system.

## <a name="opt-out-of-data-collection"></a>Opcja rezygnacji z zbierania danych

Podane dane, które zbieramy i ograniczenia dotyczące jego dostępu i przechowywania, zalecane jest użycie domyślnych ustawień prywatności dla programu Visual Studio i Windows. Można jednak [zrezygnować](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) z programu poprawy jakości obsługi programu Visual Studio. Aby zrezygnować z kolekcji dziennika generowanych przez system dla wszystkich programów, zobacz [diagnostyki, opinie i ochrona prywatności w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Opcje mogą się różnić w zależności od wersji systemu Windows używasz.

## <a name="see-also"></a>Zobacz także

- [Program poprawy jakości obsługi klienta systemu Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostyka, opinie i ochrona prywatności w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)