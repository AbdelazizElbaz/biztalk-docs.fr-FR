---
title: SchemaValidator | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, SchemaValidator utility
- validating, SchemaValidator utility
- SchemaValidator utility
- schemas, SchemaValidator utility
ms.assetid: 3bd61a03-d81e-4fd1-802c-f801000002d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c25615c2efcb37ebfc6083bc09d48c7fc1506217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schemavalidator"></a>SchemaValidator
Vous utilisez l’utilitaire SchemaValidator pour résoudre les problèmes liés à une instance de message. Si vous recevez un message dont la validation échoue, vous pouvez exécuter l’utilitaire SchemaValidator pour déterminer la source de l’échec.  
  
 Vous utilisez cet utilitaire si vous utilisez un assembly qui inclut un fichier de schéma, et vous n’avez pas d’un fichier .xsd de schéma. L’utilitaire SchemaValidator vous permet de valider à l’aide du fichier .dll de schéma.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\SchemaValidator  
  
## <a name="building-and-running-schemavalidator"></a>Génération et exécution SchemaValidator  
  
#### <a name="to-build-the-schemavalidator-utility"></a>Pour générer l’utilitaire SchemaValidator  
  
1.  Ouvrez une invite de commandes.  
  
2.  Déplacer vers \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\SchemaValidator.  
  
3.  À l’invite de commandes, tapez **sn -k SchemaValidator.snk**, puis appuyez sur ENTRÉE.  
  
4.  Démarrez **Microsoft Visual Studio 2012**.  
  
5.  Sur le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **ouvrir une Solution**.  
  
6.  Déplacer vers \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\SchemaValidator, sélectionnez **SchemaValidator.sln**, puis Cliquez sur **ouvrir**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **SchemaValidator**, puis cliquez sur **propriétés**.  
  
8.  Dans la page **Propriété de MessageInspector**  , cliquez sur l'onglet **Signature** , puis cochez la case **Signer l'assembly** . Sélectionnez **SchemaValidator.snk** dans **choisir un fichier de clé de nom fort**.  
  
9. Cliquez sur **SchemaValidator.cs**.  
  
10. Tapez le chemin d’instance de message approprié dans la ligne de code existante suivante `Main`:  
  
    ```  
    const string xmlInstancePath = @"..\..\Sample3A4.xml";  
    ```  
  
11. Remplacez la ligne suivante existante du code dans `Main` avec une référence à l’assembly RNPIPs, puis sélectionnez le schéma approprié :  
  
    ```  
    _3A4_MS_V02_02_PurchaseOrderRequest BTSSchema = new _3A4_MS_V02_02_PurchaseOrderRequest();  
    ```  
  
12. Avec le bouton droit **SchemaValidator**, puis cliquez sur **Build**.  
  
13. Modifier l’instance de message pour que vous souhaitez tester en supprimant le \< \!DOCTYPE... > balise en spécifiant le fichier DTD à partir de l’en-tête de l’instance XML.  
  
14. Dans le nœud racine de l’instance de message, ajoutez un espace de noms XML du schéma que vous allez valider par rapport à.  
  
    > [!NOTE]
    >  Pour obtenir un exemple d’un schéma prêt à être validée par l’utilitaire SchemaValidator, consultez Sample3A4.xml dans \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\ SchemaValidator.  
  
15. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **SchemaValidator.cs**, puis appuyez sur CTRL et sur F5 pour exécuter l’utilitaire.  
  
## <a name="remarks"></a>Notes  
 Étant donné que le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut le code SchemaValidator, vous pouvez ajouter une logique à l’utilitaire. Par exemple, vous pouvez rendre un utilitaire de ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)