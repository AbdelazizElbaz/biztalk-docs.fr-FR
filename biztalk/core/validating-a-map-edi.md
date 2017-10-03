---
title: "Validation d’un mappage (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caf58ecf-ed10-4c13-8d7d-e007b9158b0e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 028a152be285bb79f3cd0899b2143e99ef2b6042
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-map-edi"></a>Validation d'un mappage (EDI)
Vous pouvez valider un mappage lors de la phase de conception. Pour ce faire, vous utilisez les extensions de l’outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environnement. Cette opération a pour effet de générer un fichier contenant le XSLT sous-jacent du mappage ainsi qu'un autre fichier contenant les objets d'extension.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-validate-a-map"></a>Pour valider un mappage  
  
1.  Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Dans l'Explorateur de solutions, ajoutez le mappage que vous souhaitez valider ainsi que les schémas de messages entrant et sortant.  
  
    > [!NOTE]
    >  Ces derniers se trouvent dans le sous-dossier approprié, sous le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI. Pour plus d’informations sur l’installation des fichiers de schéma, consultez [comment installer les fichiers de schéma EDI](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).  
  
    > [!NOTE]
    >  Il est inutile de générer un projet pour valider un mappage.  
  
2.  Avec le bouton droit de la carte dans l’Explorateur de solutions, puis cliquez sur **valider le mappage**.  
  
3.  Vérifiez qu'il y a un message dans la fenêtre Sortie indiquant que l'opération a réussi.  
  
4.  Notez les avertissements qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a validé dans le **sortie** fenêtre.  
  
5.  Dans le **sortie** fenêtre, notez le nom et le chemin d’accès de la sortie XSLT. Ce fichier XSL possède le même nom que le fichier de mappage, mais avec une extension XSL. Vous pouvez appuyer sur CTRL et cliquer sur le lien pour afficher le fichier XSL dans l'Éditeur BizTalk.  
  
6.  Dans le **sortie** fenêtre, notez le nom et le chemin d’accès de l’objet d’extension XML. Vous pouvez appuyer sur CTRL et cliquer sur le lien pour afficher le fichier XSL dans l'Éditeur BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)