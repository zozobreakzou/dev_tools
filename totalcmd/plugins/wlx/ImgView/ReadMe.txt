----------------------------------------------------------------

ImgView.wlx   V 1.0   2006-03-15   (C) M. Diegelmann

----------------------------------------------------------------


English:
========

Total Commander lister plugin for displaying the image file types 
ANI, BMP, CUR, EMF, EPS, GIF, ICO, JPEG, JPG, PCX, PIC, PNG, PSD, 
PSP, SCR, SGI, TGA, THM, TIF and WMF by pressing the F3 function 
key or Ctrl+Q (Quick View).

----------------------------------------------------------------

Installation:


a) The easy way (works with Total Commander version 6.5 or later)

   Run Total Commander and open the download file ImgView.zip by 
   a double click. This executes the file PlugInst.inf contained 
   in this zip file and will install the lister plugin ImgView 
   automatically. A previously installed version of ImgView will 
   be overwritten and therefore doesn't have to be uninstalled 
   first. However, if the new version supports a wider selection 
   of image file types than the old version did, the old version 
   must be uninstalled manually before installing the new one 
   (Total Commander menu items Configuration -> Options -> Ope-
   rations/Plugins -> group box Lister plugins -> buttons Confi-
   gure and Remove).


b) The hard way

1. If a subdirectory for lister plugins does not yet exist in 
   the Total Commander program directory (e.g. the directory
   C:\Program Files\TotalCmd), such a subdirectory (preferably 
   named Plugins\WLX) has to be created there in a first step. 
   Then create the directory ImgView in Plugins\WLX and finally 
   copy to this newly created subdirectory the dynamic link lib-
   rary ImgView.wlx packed into ImgView.zip.

2. Call the Total Commander menu items Configuration -> Settings 
   to open the Configuration window with a tree view of configu-
   ration items and click the node Operation-Plugins. In the 
   group box Lister Plugins (*.WLX) press the Configure button. 
   A Lister-Plugins window will pop up with a list of all pre-
   viously installed plugins.
   
3. In case an earlier version of ImgView has already been in-
   stalled, this one has to be uninstalled prior to installing 
   the new version (highlight the respective entry in the list 
   and then click the Remove button).

4. Clicking the Add button will invoke an open file dialog box. 
   Navigate to the ...\Plugins\WLX\ImgView directory created in 
   step 1 and select the ImgView.wlx dynamic link library.

5. Close both the Lister-Plugins window and the Configuration 
   window by pressing their OK buttons. Total Commander will 
   automatically save this new confiruration to its wincmd.ini 
   file. (The menu items Configuration -> Save settings need 
   not be called explicitly for this purpose.)


This installation procedure applies to Total Commander versions 
6.5 and higher. With older versions the installation of lister 
plugins is started from within the lister (invoked by F3) itself 
by means of the Options -> Configuration menu items opening the 
Lister Configuration window and by clicking the LS plugins but-
ton contained in this window. After this continue with steps 3 
to 5 of the above procedure.

IMPORTANT: To enable the display of *.EMF and *.WMF files add 
           the line "WmfAllowed=3" to the [Configuration] sect-
           ion of the wincmd.ini file.

----------------------------------------------------------------

Operation:

1. The context pop-up menu of the lister window to be invoked by 
   a right mouse button click provides a choice of the following 
   actions:

   a) Copy the currently displayed image to the clipboard (also 
      possible by means of the somewhat misleadingly named lister 
      menu item Edit -> Copy as text as well as with the keyboard 
      shortcut Ctrl+C).
   b) Print the currently displayed image.
   c) The setting of the background color.
   d) The setting of the initial positioning of the image in the 
      lister window (aligned at the top left corner or centered)
   e) The settings of the image resizing rules to fit the window 
      size (separately for stretching images which are smaller 
      than the display window and for shrinking images which are 
      larger than the display window).
   f) The setting of the option for image auto-orientation accor-
      ding to the orientation information contained in the Exif 
      meta data.
   g) The setting of the ImgView error message display option.
   h) The selection of the file types to be displayed by ImgView 
      (the currently supported file types are: ANI, BMP, CUR, 
      EMF, EPS, GIF, ICO, JPEG, JPG, PCX, PIC, PNG, PSD, PSP, 
      SCR, SGI, TGA, THM, TIF and WMF).

2. The image resizing rules can also be set using the main menu 
   of the Total Commander lister itself (menu items Options -> 
   Fit image to window size). If at the time of checking this 
   menu item an image is being displayed which is smaller than 
   the lister window client area, the ImgView plugin will take 
   this setting as the stretch small images to window size flag. 
   If, however, an image is being displayed which is larger than
   the lister window client area, the ImgView plugin will take 
   this setting as the shrink large images to window size flag. 
   Depending on which one of the two resizing rules (shrink lar-
   ge images or stretch small images) is currently effective, 
   the activation state of this particular rule will be toggled 
   ON and OFF upon double-clicking the lister window. When mag-
   nifying a shrunk image to its original size by double-click-
   ing the image area, the point clicked will be the fixed point 
   of this magnification.

3. Images can be moved across the lister window in a number of 
   ways. Independent of their size they can always be dragged by
   mouse. Additionally, images which are larger than the lister 
   window can also be scrolled in the ususal way by means of the
   following navigation keys: Cursor Up/Down/Left/Right, Home, 
   End, Ctrl+Home and Ctrl+End.

4. If a number of files is highlighted in the Total Commander 
   file list, this group of files can be browsed either by the 
   PgUp and PgDown keys or by mouse wheel (same effect as the 
   two keys 'P' and 'N' known from the TC built-in lister).

5. ImgView is a small plugin for Total Commander. It is primari-
   ly designed as a quick view utility to be used in image file 
   administration activities (copy, move, delete, rename, find 
   particular images etc.) - not more. Users having more deman-
   ding things in mind (e.g. the display of animated cursors ANI, 
   the manipulation of picture data etc.) should use some commer-
   cial program (IrfanView, ACDSee-Viewer or similar) specially 
   designed for this kind of job. The Total Commander built-in 
   lister itself allows for using the IrfanView and XnView pro-
   grams as a lister replacement (menu Options -> Configure, 
   check box Use IrfanView/XnView to load graphics other than 
   BMP).

----------------------------------------------------------------

Author:

   Michael Diegelmann
   Fachhochschule Rosenheim
   Fakultaet Angewandte Natur- und Geisteswissenschaften
   Hochschulstrasse 1
   D-83024 Rosenheim
   Germany

   e-Mail: Michael.Diegelmann@gmx.de

----------------------------------------------------------------


Deutsch:
========

Total Commander Lister-Plugin zur Anzeige folgender Dateitypen:
ANI, BMP, CUR, EMF, EPS, GIF, ICO, JPEG, JPG, PCX, PIC, PNG, PSD, 
PSP, SCR, SGI, TGA, THM, TIF und WMF mit der Funktionstaste F3 
bzw. mit Strg+Q (Schnellansicht).

----------------------------------------------------------------

Installation:


a) Schnellmethode (funktioniert ab Total Commander Version 6.5)

   Im Total Commander die Download-Datei ImgView.zip mit einem 
   Doppelklick öffnen. Dadurch wird die darin enthaltene Datei 
   PlugInst.inf ausgewertet und der Lister-Plugin ImgView voll-
   automatisch installiert. Dabei wird eine früher installierte 
   ImgView-Version einfach überschrieben und muss daher norma-
   lerweise nicht zuvor gelöscht werden. Falls jedoch die neue 
   Version eine größere Auswahl an Bild-Dateitypen unterstützt 
   als die alte Version, muss diese ältere Version zuvor unbe-
   dingt aus dem Total Commander heraus deinstalliert werden 
   (Menü Konfigurieren -> Einstellungen -> Operation/Plugins 
   -> Group Box Lister-Plugins -> Buttons Konfigurieren und 
   Entfernen).


b) Zu Fuß

1. Sofern unter dem Total Commander-Programmverzeichnis (z.B. 
   C:\Programme\TotalCmd) noch kein Unterverzeichnis zur Auf-
   nahme von Lister-Plugins existiert, ist an dieser Stelle ein 
   solches Verzeichnis (z.B. Plugins\WLX) einzurichten. Danach 
   ist darunter ein Verzeichnis ImgView zu erzeugen und anschlie-
   ßend ist die in ImgView.zip gepackte DLL ImgView.wlx in dieses 
   Verzeichnis zu kopieren.

2. Im Total Commander mit der Menüfolge Konfigurieren -> Einstel-
   lungen das Fenster Konfigurieren aufrufen und in dem darin 
   erscheinenden Baum den Knoten Operation/Plugins anklicken. 
   In der dadurch angezeigten Group Box Lister-Plugins (*.WLX) 
   den Button Konfigurieren anklicken. Daraufhin erscheint ein 
   Fenster Lister-Plugins mit einer Liste aller bis dahin schon 
   installierten Plugins.

3. Sollte bereits eine ältere Version von ImgView.wlx instal-
   liert sein, ist diese zuvor zu deinstallieren (in der Liste 
   markieren und den Button Entfernen anklicken).

4. Den Button Hinzufügen anklicken und mit dem dann erscheinen-
   den FileOpen-Dialog die zuvor in Schritt 1 in das Verzeichnis 
   ...\Plugins\WLX\ImgView kopierte DLL-Datei namens ImgView.wlx 
   auswählen.

5. Die Fenster Lister-Plugins und Konfigurieren jeweils mit dem 
   Button OK schließen. Diese neue Konfiguration wird vom Total 
   Commander automatisch in seiner INI-Datei gespeichert. (Die 
   Menüfolge Konfigurieren -> Einstellungen speichern muss hier-
   zu nicht explizit aufgerufen werden.)


Diese Anleitung beschreibt die Installation des Lister-Plugins 
für den Total Commander ab Version 6.5. Bei früheren Versionen 
erfolgt die Installation von Lister-Plugins aus dem mit F3 auf-
gerufenen Lister heraus mit der Menüfolge Optionen -> Konfigu-
rieren und einem Klick auf den Button LS-Plugins des damit ge-
öffneten Fensters Lister Konfigurieren. Danach ist mit den oben 
angegebenen Schritten 3. bis 5. fortzufahren.

ACHTUNG: Um die Anzeige von *.EMF- und *.WMF-Dateien zu akti-
         vieren, muss die Zeile "WmfAllowed=3" in die Sektion 
         [Configuration] der Total Commander-Initialisierungs-
         datei wincmd.ini eingefügt werden.

----------------------------------------------------------------

Benutzung:

1. Das durch einen Rechtsklick in das Listerfenster aufzurufende 
   Kontext-Popup-Menü gestattet die Auswahl einer der folgenden 
   Aktionen:

   a) Das Kopieren des angezeigten Bilds in die Zwischenablage 
      (auch möglich über den im Zusammenhang mit Bild-Dateien 
      etwas missverständlich klingenden Lister-Menüpunkt Bear-
      beiten -> Als Text kopieren sowie mit Hilfe des Tastatur-
      Shortcuts Strg+C).
   b) Das Drucken des angezeigten Bilds.
   c) Die Festlegung der Hintergrundfarbe.
   d) Die Einstellung der anfänglichen Positionierung des Bilds 
      innerhalb des Lister-Fensters (in der linken oberen Ecke 
      oder zentriert).
   e) Die Festlegung der Bildgrößenanpassung an die Fenstergröße, 
      und zwar getrennt für Bilder, die kleiner sind als das Lis-
      ter-Fenster und für solche, die größer als dieses Fenster 
      sind.
   f) Die Festlegung der Option zur automatischen Orientierung 
      der Bilder gemäß der in den Exif-Metadaten enthaltenen 
      Lageinformation.
   g) Die Festlegung der Option zur Anzeige der ImgView-Fehler-
      meldungen.
   h) Die Auswahl der anzuzeigenden Dateitypen 
      (derzeit unterstützte Dateitypen:   ANI, BMP, CUR, EMF, 
      EPS, GIF, ICO, JPEG, JPG, PCX, PIC, PNG, PSD, PSP, SCR, 
      SGI, TGA, THM, TIF und WMF).

2. Die Festlegung der Bildgröße kann auch über das Hauptmenü des 
   Total Commander-Listers erfolgen (Menüfolge: Optionen -> Bild 
   der Fenstergröße anpassen). Ist beim Anklicken dieses Menü-
   punkts ein Bild geladen, das kleiner ist als das Lister-Fens-
   ter, dann übernimmt der ImgView-Plugin diese Einstellung für 
   die Bildgrößenanpassung der zu kleinen Bilder. Ist dagegen 
   ein zu großes Bild geladen, dann wird diese Lister-Einstel-
   lung von ImgView für die Größenanpassung der zu großen Bilder 
   übernommen. Abhängig von aktuell wirksamen Methode der Bild-
   größenanpassung (zu kleine Bilder strecken oder zu große Bil-
   der stauchen) wird die Aktivierung dieser Methode durch einen 
   Doppelklick in das Lister-Fenster ein- bzw. ausgeschaltet 
   (Toggle). Beim Vergrößern gestauchter Bilder auf ihre Origi-
   nalgröße durch einen Doppelklick in das Bild ist der dabei an-
   geklickte Punkt der Fixpunkt dieser Vergrößerungsoperation.

3. Die angezeigten Bilder lassen sich auf verschiedene Arten in-
   nerhalb des Lister-Fensters verschieben. Unabhängig von ihrer 
   Größe können sie jederzeit mit der Maus gegriffen und bewegt 
   werden. Bilder, die größer als das Lister-Fenster sind, lassen 
   sich auf die übliche Weise mit den folgenden Navigationstasten 
   scrollen: Cursor auf/ab/links/rechts, Pos1, Ende, Strg+Pos1 
   und Strg+Ende.

4. Wenn in der Datei-Liste des Total Commander mehrere Dateien 
   markiert sind, dann kann man mit den beiden Tasten Bild-auf 
   und Bild-ab bzw. mit dem Mausrad durch diese Datei-Liste 
   browsen (gleiche Wirkung wie die Tasten 'P' und 'N' des im 
   Total Commander integrierten Listers).

5. ImgView ist ein kleines Zusatzprogrammm zum Total Commander. 
   Es soll hauptsächlich dazu dienen, beim Verwalten von Bild-
   Dateien (kopieren, verschieben, löschen, umbenennen, nach 
   bestimmten Bildern suchen etc.) einen kurzen Einblick in 
   deren Inhalt nehmen zu können - mehr nicht. Wer noch weiter-
   gehende Anforderungen stellt (z.B. die Anzeige von animierten 
   ANI-Cursorn, Bildbearbeitung etc.), sollte dazu ein eigens 
   für solche Aufgaben entwickeltes Anwenderprogramm (IrfanView, 
   ACDSee-Viewer o.ä.) verwenden. Die Verwendung der Programme 
   IrfanView und XnView als Lister-Ersatz ist sogar direkt in 
   dem im Total Commander integrierten Lister einstellbar (Menü 
   Optionen -> Konfigurieren, Checkbox Benutze IrfanView/XnView 
   für andere Grafiken als BMP).

----------------------------------------------------------------

Autor:

   Michael Diegelmann
   Fachhochschule Rosenheim
   Fakultaet Angewandte Natur- und Geisteswissenschaften
   Hochschulstraße 1
   83024 Rosenheim

   E-Mail: Michael.Diegelmann@gmx.de

----------------------------------------------------------------
