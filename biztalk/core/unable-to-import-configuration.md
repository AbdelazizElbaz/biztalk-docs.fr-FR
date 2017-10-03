---
title: "Impossible d’importer la configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2887da50-4f74-4259-a7d6-c87bc9b9fc58
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e565b466e4f9ce8af3745948952b4318a029ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-configuration"></a>Impossible d'importer la configuration
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'importer la configuration à partir du fichier « {0} »|  
  
## <a name="explanation"></a>Explication  
 Plusieurs raisons peuvent expliquer cette erreur :  
  
-   Le fichier de configuration peut contenir des caractères non valides par rapport au codage donné.  
  
-   L'élément racine est peut-être manquant.  
  
-   Les données au niveau racine sont peut-être non valides.  
  
> [!NOTE]
>  Cette situation et l'action de l'utilisateur s'appliquent uniquement aux adaptateurs WCF-Custom et WCF-CustomIsolate.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet d'importer un fichier de configuration valide.  
  
#### <a name="to-import-a-valid-configuration-file"></a>Pour importer un fichier de configuration valide  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Import/Export** onglet.  
  
9. Cliquez sur **Importer**. Importez un fichier de configuration valide et complet.  
  
 Vous pouvez également vérifier la validité du fichier de configuration en l’ouvrant avec l’éditeur de Configuration de Service **(Démarrer > tous les programmes > Kit de développement)** (cette étape suppose que vous avez installé le kit SDK Windows.) Ouvrez **svcConfigEditor.exe** et vérifiez chaque propriété du fichier de configuration.