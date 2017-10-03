---
title: "Génération d’une Instance (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362b9803-4d4a-4d17-9ad6-439ec4c7d8aa
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5696d1590859469b10def4a42c955ff098819d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-instance-edi"></a>Génération d'une instance (EDI)
Vous pouvez générer une instance de message à partir d'un schéma EDI au moment de la conception. Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 Vous pouvez générer soit un échange par lot complet (avec des en-têtes d'échange et de groupe) soit un document informatisé (avec en-tête d'échange et de groupe). Si vous exécutez l'opération pour générer un échange complet, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produit un fichier contenant un en-tête d'échange, un groupe pour chaque schéma et trois documents informatisés identiques par groupe pour chaque schéma. Si vous exécutez l'opération pour générer un document informatisé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produit un fichier contenant un seul document informatisé.  
  
 Pour générer un échange par lot complet, vous exécutez la commande Générer-instance sur le schéma de lot. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]détecte les schémas de message dans le projet et inclut automatiquement des documents informatisés pour ces schémas.  
  
 Pour générer un document informatisé unique, vous exécutez la commande Générer-instance sur un schéma de message. Dans ce cas, le schéma de lot ne doit pas être ajouté au projet. L'instance générée n'inclut pas d'en-tête d'échange ou de groupe. Vous devez donc les ajouter manuellement pour obtenir un échange EDI opérationnel.  
  
 Lorsque vous générez une instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche une boîte de dialogue dans laquelle vous spécifiez la configuration de celle-ci, notamment les séparateurs et l'identificateur de syntaxe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-generate-an-instance-of-a-batched-interchange"></a>Pour générer une instance d'un échange par lot  
  
1.  Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Ajoutez un schéma de message au projet dans l'Explorateur de solutions pour chaque type de document informatisé que vous voulez dans l'instance de message. Ajoutez le schéma de lot pour le type de codage au projet : Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd.  
  
    > [!NOTE]
    >  Les schémas de lot sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.  
  
    > [!NOTE]
    >  Il est inutile de créer le projet pour générer une instance.  
  
2.  Cliquez sur le schéma de lot dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés** , configurez **Type sortie générer l’Instance** à **natif** ou **XML**. En sélectionnant **natif** vous invite à la génération d’un fichier plat avec une extension .txt. En sélectionnant **XML** vous invite à la génération d’un fichier XML.  
  
4.  Pour **nom de fichier de sortie Instance**, entrez un nom ou accédez à un fichier et sélectionnez le fichier.  
  
    > [!NOTE]
    >  Si vous n'entrez pas de valeur pour le nom de fichier d'instance de sortie, le système en choisit une à votre place. Le nom de fichier s'affiche dans la fenêtre Sortie de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  Si vous sélectionnez un fichier existant, son contenu est remplacé par celui généré par cette opération.  
  
5.  Cliquez sur le schéma de lot, puis sur **générer l’Instance**.  
  
6.  Dans le **propriétés de l’Instance EDI** boîte de dialogue, sélectionnez les séparateurs, les identificateurs et les autres configuration options à être utilisé dans cette instance, puis cliquez sur **OK**.  
  
7.  Vérifiez que l’opération a fonctionné le **sortie** fenêtre.  
  
8.  Pour afficher le fichier, appuyez sur **contrôle** et cliquez sur le lien dans le **sortie** fenêtre. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]Affiche le contenu du fichier dans la fenêtre de l’Éditeur BizTalk.  
  
    > [!NOTE]
    >  Lorsque vous générez une instance qui contient un 837I, 837d ou 837p, la valeur de GS08 est incorrectement définie sur 00401. Pour plus d’informations, consultez [problèmes connus avec les outils de XML utilisés avec les Solutions EDI](../core/known-issues-with-xml-tools-used-with-edi-solutions.md).  
  
### <a name="to-generate-an-instance-of-a-transaction-set"></a>Pour générer une instance d'un document informatisé  
  
1.  Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Ajoutez le schéma pour le type de document informatisé pour lequel vous voulez générer une instance.  
  
    > [!NOTE]
    >  Il est inutile d'ajouter le schéma de lot au projet pour générer une instance d'un document informatisé.  
  
    > [!NOTE]
    >  Il est inutile de créer le projet pour générer une instance.  
  
2.  Cliquez sur le schéma de message dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
3.  Dans la fenêtre Propriétés, définissez **Type sortie générer l’Instance** à **natif** ou **XML**. En sélectionnant **natif** vous invite à la génération d’un fichier plat avec une extension .txt. En sélectionnant **XML** vous invite à la génération d’un fichier XML.  
  
4.  Pour **nom de fichier de sortie Instance**, entrez un nom ou accédez à un fichier et sélectionnez le fichier.  
  
    > [!NOTE]
    >  Si vous n'entrez pas de valeur pour le nom de fichier d'instance de sortie, le système en choisit une à votre place. Le nom de fichier s’affichera dans le **sortie** fenêtre de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  Si vous sélectionnez un fichier existant, son contenu est remplacé par celui généré par cette opération.  
  
5.  Cliquez sur le schéma de message, puis sur **générer l’Instance**.  
  
6.  Dans le **propriétés de l’Instance EDI** boîte de dialogue, sélectionnez les options de configuration que vous souhaitez, puis cliquez sur **OK**.  
  
7.  Vérifiez qu’il existe un message dans le **sortie** fenêtre, indiquant que l’opération a réussi.  
  
8.  Pour afficher le fichier, appuyez sur **contrôle** et cliquez sur le lien dans la fenêtre Sortie. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Affiche le contenu du fichier dans la fenêtre de l’Éditeur BizTalk.  
  
9. Pour créer un message EDI opérationnel, dans l'éditeur de texte, ajoutez les en-têtes d'échange et de groupe au message.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)   
 [Validation d’une Instance (EDI)](../core/validating-an-instance-edi.md)