---
title: "Annexe c : fichiers CAB redistribuables | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2049d61-e169-4b30-869a-33d5af097941
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1a1f2b6866a2841abaa248479430a7584db3a0b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="appendix-c-redistributable-cab-files"></a>Annexe C : Fichiers CAB redistribuables
Ces fichiers CAB sont utilisés par le programme d’installation de BizTalk Server.

## <a name="biztalk-2016-cab-files"></a>Fichiers CAB de BizTalk 2016

|Langage|Télécharger le lien|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2016 : [http://go.microsoft.com/fwlink/p/?LinkId=746413](http://go.microsoft.com/fwlink/p/?LinkId=746413)</li><li>Windows Server 2012 R2 : [http://go.microsoft.com/fwlink/p/?LinkId=746412](http://go.microsoft.com/fwlink/p/?LinkId=746412)</li><li>Windows 10 : [http://go.microsoft.com/fwlink/p/?LinkId=746408](http://go.microsoft.com/fwlink/p/?LinkId=746408)</li><li>Windows 8.1 : [http://go.microsoft.com/fwlink/p/?LinkId=746411](http://go.microsoft.com/fwlink/p/?LinkId=746411)</li></ul></li><li>**X32**<br /><br /><ul><li>Windows 10 : [http://go.microsoft.com/fwlink/p/?LinkId=746409](http://go.microsoft.com/fwlink/p/?LinkId=746409)</li><li>Windows 8.1 : [http://go.microsoft.com/fwlink/p/?LinkId=746410](http://go.microsoft.com/fwlink/p/?LinkId=746410)</li></ul></li></ul>|  

> [!NOTE] 
> Windows 10 et Windows Server 2016 utilisent les mêmes fichiers CAB que Windows 8.1 et Windows Server 2012 R2. Par conséquent, ils ont le même nom de fichier.

## <a name="biztalk-2013-r2-and-2013-cab-files"></a>Fichiers CAB de BizTalk 2013 R2 et 2013  
  
|Langage|Télécharger le lien|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2012 : [http://go.microsoft.com/fwlink/p/?LinkId=269616](http://go.microsoft.com/fwlink/p/?LinkId=269616)</li><li>Windows Server 2008 : [http://go.microsoft.com/fwlink/p/?LinkId=269613](http://go.microsoft.com/fwlink/p/?LinkId=269613)</li><li>Windows 8 : [http://go.microsoft.com/fwlink/p/?LinkId=269615](http://go.microsoft.com/fwlink/p/?LinkId=269615)</li><li>Windows 7 : [http://go.microsoft.com/fwlink/p/?LinkId=269614](http://go.microsoft.com/fwlink/p/?LinkId=269614)</li></ul></li><li>**X32**<br /><br /> <ul><li>Windows 8 : [http://go.microsoft.com/fwlink/p/?LinkId=269612](http://go.microsoft.com/fwlink/p/?LinkId=269612)</li><li>Windows 7 : [http://go.microsoft.com/fwlink/p/?LinkId=269611](http://go.microsoft.com/fwlink/p/?LinkId=269611)</li></ul></li></ul>|  
  
## <a name="important-info"></a>Informations importantes

- SQL XML peut avoir sa propre configuration logicielle requise (telle que `.NET Framework 3.5` et `.NET Framework 2.0`), qui n’est pas incluse dans le fichier CAB. Si le serveur BizTalk Server a accès à Internet, la configuration logicielle requise pour SQL XML peut être installée automatiquement. Si le serveur BizTalk Server n’a pas accès à Internet, installez manuellement la configuration logicielle requise pour SQL XML.

- Les chemins d’installation du fichier CAB sont également répertoriés dans le **Setup.xml** fichier dans le dossier d’installation ([!INCLUDE[btsBizTalkServerPathx64_md](../includes/btsbiztalkserverpathx64-md.md)]\<votre version\>).
  
-   Certains logiciels requis par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont installés sur votre ordinateurs avant l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous donne la possibilité de télécharger les logiciels prérequis à partir du Web ou de les extraire de vos fichiers CAB. Si vous choisissez les fichiers CAB, téléchargez-les avant d'exécuter l'installation.  
  
-   Vous ne pouvez pas utiliser les fichiers CAB des versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez télécharger les fichiers CAB à partir des liens du tableau.  
  
-   Vous ne pouvez pas télécharger les fichiers CAB via une session Telnet.  