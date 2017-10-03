---
title: "Étape 2 : Créer et déployer l’exemple X12 schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5862168-6621-40ab-8c97-3f317530d34e
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe4f937af910ceef1ed461e25ea3c62cad5cbc29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-and-deploy-the-sample-x12-schema"></a>Étape 2 : Créer et déployer l’exemple X12 schéma
![Étape 2 sur 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")  
  
 Au cours de cette étape, vous allez créer et déployer le projet qui fournit un exemple de schéma EDI X12 requis pour traiter l'échange EDI X12 entrant transporté via AS2. Pour ce didacticiel, ce schéma est X12_00401_864.xsd. Vous ne devez pas modifier le projet fourni avec le didacticiel AS2. Vous devez juste le générer.  
  
> [!NOTE]
>  Le fichier de schéma X12_00401_864.xsd que ce didacticiel utilise est stocké dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] SDK\AS2 Tutorial\Schemas. Il a déjà été ajouté au projet Schémas que vous allez créer et déployer au cours de cette étape. Ce schéma est différent du fichier X12_00401_864.xsd téléchargé sur votre ordinateur en exécutant MicrosoftEdiXsdTemplates.exe dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI. Le didacticiel ne fonctionnera que si vous utilisez le fichier X12_00401_864.xsd qui a été ajouté à Schemas.btproj.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-and-deploy-the-sample-x12-schema"></a>Pour créer et déployer l'exemple de schéma X12  
  
1.  Démarrer **Microsoft Visual Studio** en tant qu’administrateur.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez la solution [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
3.  Cliquez sur le projet de schémas, puis cliquez sur **propriétés**. Cliquez sur le **signature** onglet Concepteur de projets. Vérifiez le **signer l’Assembly** case à cocher, pour **choisir un fichier de nom fort de la clé**, sélectionnez  **\<nouveau... >** et entrez `Schemas.snk`. Désactivez **protéger mon fichier de clé avec un mot de passe** puis cliquez sur **OK**. Fermez la page des propriétés du projet et enregistrez les modifications.  
  
4.  Créez et déployez Schemas.btproj.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez un tiers et un profil métier de votre organisation (Contoso), comme décrit dans [étape 3 : configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas de Document EDI](../core/edi-document-schemas.md)