---
title: "Déployer et tester l’application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2c86d5f-1849-4b7d-8061-23f156245f5b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56b390ef87ac2ea58d91be2ff16a50f2c3748db2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploy-and-test-the-application"></a>Déployer et tester l'application
> [!NOTE]
>  Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].  
  
 Dans cette rubrique, nous allons générer, déployer, configurer et tester l’application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="build-and-deploy-the-application"></a>Créer et déployer l'application  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk, puis cliquez sur **propriétés**.  
  
2.  Dans la page Propriété, cliquez sur l'onglet Signature, activez la case à cocher Signer l'assembly, puis dans la liste déroulante choisissez l'option permettant de créer un nouveau fichier de clé de nom fort. Suivez les instructions pour créer le fichier.  
  
3.  Enregistrez les modifications apportées au projet. Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.  
  
4.  Une fois le projet construit avec succès, dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="configure-the-application"></a>Configurez l'application  
 Pour configurer l'application, dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], créez les ports d'envoi et de solution, puis reliez-les à l'orchestration et aux ports Envoi/Réception logiques créés dans le cadre de l'orchestration.  
  
1.  Créez un port de réception à travers lequel un bon de commande JSON est reçu par l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    1.  Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **BizTalk Application 1**, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
    2.  Fournissez un nom pour le port de réception, puis dans le volet gauche, cliquez sur **emplacements de réception**. Dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
    3.  Spécifiez un nom pour l’emplacement de réception, sélectionnez le type de port **fichier**, puis cliquez sur **configurer**.  
  
    4.  Indiquez l'emplacement du dossier où l'emplacement de réception enlèvera le bon de commande JSON entrant. Spécifiez `*.json` en tant que le masque de fichier, puis cliquez sur **OK**.  
  
    5.  À partir de la **Pipeline de réception** liste déroulante, sélectionnez **JSONToXml**. Vous avez créé ce pipeline de réception personnalisé dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur le bouton de sélection **(...)**  bouton suivant pour le pipeline, puis sous **étape 1 – Deocde Component**, indiquez les valeurs suivantes :  
  
        -   RootNode-`ROOT`  
  
        -   RootNodeNamespace –`http://BTSJSON`.  
  
         Ces valeurs représentent l'espace de noms cible et le nom de nœud racine du schéma du bon de commande XML qui a été généré à partir du bon de commande JSON via l'Assistant Schéma de JSON.  
  
    6.  Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.  
  
2.  Créez un port d'envoi pour l'envoi de messages de la facture JSON.  
  
    1.  Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **BizTalk Application 1**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel**.  
  
    2.  Spécifiez un nom pour le port d’envoi, sélectionnez le type de port **fichier**, puis cliquez sur **configurer**.  
  
    3.  Indiquez l'emplacement du dossier où le port d'envoi copie la facture JSON sortante. Spécifiez `%MessageID%.json` comme le nom de fichier puis cliquez sur **OK**.  
  
    4.  À partir de la **Pipeline d’envoi** liste déroulante, sélectionnez **XmlToJSON**, puis cliquez sur **OK**.  
  
    5.  Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.  
  
3.  Enfin, liez les ports logiques que vous avez créés dans le cadre de l'orchestration aux ports physiques que vous venez de créer pour configurer l'application.  
  
    1.  Avec le bouton droit **BizTalk Application 1**, puis cliquez sur **configurer**.  
  
    2.  Dans le volet gauche, cliquez sur **ProcessPO**. Dans le volet droit, associez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] héberger, mapper les ports logiques aux ports physiques, puis cliquez sur **OK**.  
  
    3.  Avec le bouton droit **BizTalk Application 1**, puis cliquez sur **Démarrer**.  
  
## <a name="test-the-application"></a>Tester l'application  
  
1.  Accédez à l’exemple que vous avez téléchargé et à partir de la **TestMessage** dossier, copiez **JsonPurchaseOrder.json**et le coller dans le dossier que vous avez associé à l’emplacement de réception. Attendez que le fichier disparaisse.  
  
2.  Accédez au dossier que vous avez associé au port d'envoi créé. Notez qu’un   ***\<GUID >*.json** fichier est disponible dans le dossier. Ouvrez le fichier et vérifiez qu'il s'agit du message de la facture.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)