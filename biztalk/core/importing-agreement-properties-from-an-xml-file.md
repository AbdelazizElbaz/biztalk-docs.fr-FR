---
title: "L’importation des propriétés de l’accord d’un fichier XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8bf5268-1742-47da-b42f-6472706a9bff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3ac08628931ec4111eb1b5a9ad86991344c22d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-agreement-properties-from-an-xml-file"></a>Importation des propriétés d'un accord à partir d'un fichier XML
Cette section fournit des instructions sur l'importation des propriétés d'un accord à partir d'un fichier de modèle XML.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Vous devez avoir exporté un accord dans un fichier de modèle XML, comme décrit dans [propriétés de l’accord exportation vers un fichier XML](../core/exporting-agreement-properties-to-an-xml-file.md).  
  
### <a name="to-import-agreement-properties-from-an-xml-file"></a>Pour importer les propriétés d'un accord à partir d'un fichier XML  
  
1.  Dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, cliquez sur le **Parties** nœud sous la **Administration de BizTalk Server** et **groupe BizTalk** nœuds. Dans le **tiers et profils d’entreprise** page, créez un accord, comme décrit dans [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).  
  
2.  Dans le **propriétés de l’accord** boîte de dialogue, cliquez sur **charge à partir du modèle**.  
  
    > [!NOTE]
    >  Le **charge à partir du modèle** bouton est activé uniquement après avoir sélectionné un protocole pour l’accord. Lorsque vous spécifiez le protocole, vous déclarez implicitement que vous ne pouvez importer qu'un accord pour le même protocole de codage.  
  
3.  Dans le **ouvrir** boîte de dialogue, accédez à l’emplacement du fichier XML de modèle, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
4.  Dans le **créer un modèle** , cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Réutilisation des propriétés d’un autre accord](../core/reusing-properties-from-another-agreement.md)   
 [Exportation des propriétés de l’accord vers un fichier XML](../core/exporting-agreement-properties-to-an-xml-file.md)