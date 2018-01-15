---
title: Dostosowywanie pola obrazu i tekstu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6bd4686565b24306d9c9565a5c4eddc65914f85
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-text-and-image-fields"></a>Dostosowywanie pól tekstowych i obrazu
Po zdefiniowaniu dekoratora tekstu w kształcie jest reprezentowany przez TextField. Przykłady inicjowania TextFields i innych ShapeFields Sprawdź, czy Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.  
  
 TextField jest obiekt, który zarządza obszar wewnątrz kształtu, takie jak miejsce przypisane do etykiety. Jedno wystąpienie elementu TextField jest udostępniana między wiele kształtów w tej samej klasy. Wystąpienie elementu TextField nie przechowuje tekst etykiety osobno dla każdego wystąpienia: zamiast tego `GetDisplayText(ShapeElement)` metoda pobiera kształtu jako parametr i można wyszukiwać tekst zależny od bieżącego stanu kształt i jego elementu modelu.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Jak jest określany wygląd pola tekstowego  
 `DoPaint()` Wywoływana jest metoda Wyświetla pole na ekranie. Albo można zastąpić domyślną `DoPaint(),` lub niektórych metod, które wywołuje można zastąpić. Następujące uproszczonej wersji metody domyślnej może pomóc zrozumieć sposób zastępują domyślne zachowanie:  
  
```  
// Simplified version:  
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)  
{   
  string text = GetDisplayText(shape);   
  StringFormat format = GetStringFormat(parentShape);  
  Brush brush = GetTextBrush(e.View, shape);  
  using (Font font = GetFont(shape))  
  {  
    e.Graphics.DrawString(text, font, brush, format);  
  }  
}  
// StringFormat determines whether the string is centered etc.  
// To customize statically for all instances of this shape field,   
// assign to DefaultStringFormat.  
// To customize dynamically or per shape, override this:    
public virtual StringFormat GetStringFormat(ShapeElement shape)  
{ return DefaultStringFormat; }  
  
// Override to customize the displayed string:  
public virtual string GetDisplayText(ShapeElement shape)  
{ return this.GetValue(shape).ToString(); }  
  
// Brush determines the text color.  
// To change the brush for every field, change the shape's styleset.   
// To customize to a brush in the style set, override GetTextBrushId.  
// To change the brush to non-standard color, override this.  
// Should take account of whether selected.   
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)  
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }  
  
// Brush ID selects a brush from a StyleSet.  
// Either return a member of DiagramBrushes   
// or add your own brush to the shape or application's styleset.  
// Override this to change dynamically or per instance.  
// To change statically, just assign to default values.   
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)  
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId  
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;  
}  
  
// Font determines the shape and size of the text.  
// To change the font for every field, change the shape's styleset.   
// To customize to a font in the style set, override GetFontId.  
// To change the font to a non-standard font, override this.   
public virtual Font GetFont(ShapeElement shape)  
{ return shape.StyleSet.GetFont(GetFontId(shape)); }  
  
// Selects a font from a styleset.  
// Either return a member of DiagramFonts or   
// add your own font to the shape or application's styleset.  
// To change statically for all instances of this field,   
// assign to DefaultFontId.  
// To change per shape or dynamically, override this.   
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)  
{ return DefaultFontId; }  
  
```  
  
 Istnieje kilka innych pary `Get` metod i `Default` właściwości, takie jak `DefaultMultipleLine/GetMultipleLine()`. Można przypisać wartości do właściwości domyślne można zmienić wartości dla wszystkich wystąpień pole kształtu. Aby wprowadzić wartość się różnić od wystąpienia jeden kształt do innego lub zależny od stanu kształtu lub jego element modelu, należy zastąpić `Get` metody.  
  
## <a name="static-customizations"></a>Dostosowywanie statyczne  
 Jeśli chcesz zmienić każde wystąpienie to pole kształtu, najpierw sprawdzić, czy można ustawić właściwości w definicji DSL. Na przykład w oknie właściwości można ustawić styl i rozmiar czcionki.  
  
 Jeśli nie, następnie zastąpienia `InitializeShapeFields` metody klasy kształt i przypisywanie wartości do odpowiedniego `Default...` właściwości pola tekstowego.  
  
> [!WARNING]
>  Aby zastąpić `InitializeShapeFields()`, należy ustawić **generuje podwójne pochodnych** właściwości klasy kształt, aby `true` w definicji DSL.  
  
 W tym przykładzie kształt ma pola tekstowego, który będzie używany dla komentarzy do użytkownika. Chcemy Użyj czcionki standardowe komentarza. Standardowe czcionki z zestawu stylu, dlatego firma Microsoft Ustaw domyślny identyfikator czcionki:  
  
```  
  
 partial class ExampleShape  
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Find and update comment field:  
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;  
      // Use the standard font for comments:  
      commentField.DefaultFontId = DiagramFonts.CommentText;  
  
```  
  
## <a name="dynamic-customizations"></a>Dostosowywanie na dynamiczny  
 Aby wygląd różnią się zależny od stanu kształtu lub jego element modelu, pochodzi własnych podklas `TextField` i Zastąp jeden lub więcej `Get...` metody. Należy również przesłonić metodę InitializeShapeFields Twojego kształtu i Zamień wystąpienia TextField wystąpienia własne klasy.  
  
 Poniższy przykład sprawia, że czcionka polem tekstowym jest zależny od stanu właściwość domeny Boolean elementu modelu kształtu.  
  
 Aby uruchomić ten przykład kodu, należy utworzyć nowe rozwiązanie DSL przy użyciu minimalnego języka szablonu. Dodaj właściwość domeny logiczna `AlternateState` do klasy ExampleElement domeny. Dodaj do klasy ExampleShape dekoratora ikonę i ustaw jego obrazu w pliku mapy bitowej. Kliknij przycisk **Przekształć wszystkie szablony**. Dodaj nowy plik kodu w projekcie DSL i Wstaw następujący kod.  
  
 Aby przetestować kod, naciśnij klawisz F5 i w rozwiązaniu debugowania, Otwórz przykładowy diagram. Stan domyślny ikony powinny być wyświetlane. Wybierz kształt, a następnie w oknie Właściwości zmień wartość **AlternateState** właściwości. Należy zmienić czcionkę nazwy elementu.  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
  
  partial class ExampleShape  
  {  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Replace the text field for NameDecorator:  
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;  
      shapeFields.Remove(oldField);  
      // Replace with my text field based on DSL Definition values:  
      MyTextField newField = new MyTextField(oldField);  
      shapeFields.Add(newField);  
    }  
  }  
  /// <summary>  
  /// Dynamic font depends on state of model element.  
  /// </summary>  
  public class MyTextField : TextField  
  {  
    public MyTextField(TextField prototype)  
      : base(prototype.Name)  
    {  
      DefaultText = prototype.DefaultText;  
      DefaultFocusable = prototype.DefaultFocusable;  
      DefaultAutoSize = prototype.DefaultAutoSize;  
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;  
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;  
      DefaultAccessibleState = prototype.DefaultAccessibleState;  
    }  
  
    public override System.Drawing.Font GetFont(ShapeElement parentShape)  
    {  
      // Access the Boolean domain property of the model element:  
      if ((parentShape.ModelElement as ExampleElement).AlternateState)  
        return new System.Drawing.Font("Callisto", 14.0f,  
               System.Drawing.FontStyle.Italic |   
               System.Drawing.FontStyle.Bold);  
      else  
        return base.GetFont(parentShape);  
    }  
  
  }  
  
```  
  
## <a name="style-sets"></a>Ustawia styl  
 W poprzednim przykładzie pokazano, jak można zmienić pola tekstowego do każdej czcionki, która jest dostępna. Jednakże jednak preferowaną metodą jest Zmień ją na jeden zestaw stylów skojarzonej z kształtem lub z aplikacją. Aby to zrobić, należy zastąpić <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> lub GetTextBrushId().  
  
 Alternatywnie, należy rozważyć zmianę stylu zbiór kształt przez zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Ma to wpływu zmiana czcionek i pędzle dla wszystkich pól kształtu.  
  
## <a name="customizing-image-fields"></a>Dostosowywanie pól obrazu  
 Po zdefiniowaniu dekoratora obrazu w kształcie, a podczas definiowania kształtu obrazu, obszar, w którym jest wyświetlany kształt jest zarządzana przez element ImageField. Przykłady inicjowania ImageFields i innych ShapeFields Sprawdź, czy Dsl\GeneratedCode\Shapes.cs w rozwiązaniu DSL.  
  
 Element ImageField jest obiekt, który zarządza obszar wewnątrz kształtu, takie jak miejsce przypisane do dekoratora. Jedno wystąpienie elementu ImageField jest udostępniana między wiele kształtów w tej samej klasy kształtu. Wystąpienie elementu ImageField nie przechowuje osobny obraz każdego kształtu: zamiast tego `GetDisplayImage(ShapeElement)` metoda pobiera kształtu jako parametr i można wyszukiwać obrazu zależny od bieżącego stanu kształt i jego elementu modelu.  
  
 Specjalnego zachowania przykład zmiennej obraz, można utworzyć własne klasy pochodnej z elementu ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Aby utworzyć podklasy elementu ImageField  
  
1.  Ustaw **generuje podwójne pochodnych** właściwość klasy kształtu nadrzędnego w definicji DSL.  
  
2.  Zastąpienie `InitializeShapeFields` metody klasy kształtu.  
  
    -   Utwórz nowy plik kodu w projekcie DSL i zapisać definicji klasy częściowej klasy kształtu. Zastąpienie istnieje definicja metody.  
  
3.  Sprawdź kod `InitializeShapeFields` w DSL\GeneratedCode\Shapes.cs.  
  
     W metodę zastąpienie Wywołaj metodę podstawową, a następnie utwórz wystąpienie klasy pola własnego obrazu. Umożliwia to Zastąp pole regularne obrazu w `shapeFields` listy.  
  
## <a name="dynamic-icons"></a>Dynamiczne ikony  
 W tym przykładzie powoduje, że ikona zmienić zależny od stanu elementu modelu kształtu.  
  
> [!WARNING]
>  W tym przykładzie pokazano, jak utworzyć dekoratora dynamiczny obraz. Ale jeśli chcesz przełączać się między jeden lub dwa obrazy w zależności od stanu zmiennej modelu, jest łatwiejsze utworzyć kilka elementów decorator obrazu, zlokalizuj je w tej samej pozycji kształtu, a następnie ustaw filtr widoczność są zależne od określonych wartości modelu Zmienna. Aby ustawić filtr, wybierz mapy kształtu w definicji DSL, Otwórz okno Szczegóły DSL, a następnie kliknij kartę elementów Decorator.  
  
 Aby uruchomić ten przykład kodu, należy utworzyć nowe rozwiązanie DSL przy użyciu minimalnego języka szablonu. Dodaj właściwość domeny logiczna `AlternateState` do klasy ExampleElement domeny. Dodaj do klasy ExampleShape dekoratora ikonę i ustaw jego obrazu w pliku mapy bitowej. Kliknij przycisk **Przekształć wszystkie szablony**. Dodaj nowy plik kodu w projekcie DSL i Wstaw następujący kod.  
  
 Aby przetestować kod, naciśnij klawisz F5 i w rozwiązaniu debugowania, Otwórz przykładowy diagram. Stan domyślny ikony powinny być wyświetlane. Wybierz kształt, a następnie w oknie Właściwości zmień wartość **AlternateState** właściwości. Ikona są wyświetlane obrócony do 90 stopni tego kształtu.  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
partial class ExampleShape  
{  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    /// <param name="shapeFields"></param>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
  
      // Replace the image field:  
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");  
      shapeFields.Remove(oldField);  
      // Must keep the same name:  
      MyImageField newField = new MyImageField(oldField.Name);  
      shapeFields.Add(newField);  
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;  
    }  
  }  
  
  public class MyImageField : ImageField  
  {  
    public MyImageField(string tag) : base(tag) { }  
  
    /// <summary>  
    /// Get the image for this field in the given shape.  
    /// </summary>  
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)  
    {  
      ExampleElement element = parentShape.ModelElement as ExampleElement;  
      if (element.AlternateState == true)  
        return AlternateImage;  
      else  
        return base.GetDisplayImage(parentShape);  
    }  
  
    private System.Drawing.Image alternateImage;  
    public System.Drawing.Image AlternateImage  
    {  
      get  
      {  
        if (alternateImage == null)  
        {  
          // Alternate image is a copy of the default, rotated by 90 degrees:  
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;  
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);  
        }  
        return alternateImage;  
      }  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie łączników i kształtów](../modeling/defining-shapes-and-connectors.md)   
 [Ustawienie obraz tła na diagramie](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)