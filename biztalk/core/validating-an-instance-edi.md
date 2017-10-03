---
title: "Validation d’une Instance (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fe4e87-5ab4-41e4-8ceb-8f6cf40cae0b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cceea8afe67f7e69b3ee842198d9a5373a972d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-an-instance-edi"></a>Validation d'une instance (EDI)
Vous pouvez valider une instance par rapport à son schéma EDI pendant la phase de conception. Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. L'instance que vous validez peut être un document informatisé unique (sans en-tête d'échange et de groupe), un échange comprenant un seul document informatisé (avec en-têtes d'échange et de groupe) ou un échange traité par lot complet comprenant plusieurs documents informatisés (avec en-têtes d'échange et de groupe).  
  
> [!NOTE]
>  La validation d'un échange conservé XML n'est pas prise en charge. En revanche, celle d'un échange conservé EDI l'est.  
  
 L'opération de validation de l'instance effectue la validation EDI et XSD.  
  
 Lorsque vous validez une instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche une boîte de dialogue dans laquelle vous spécifiez la configuration à valider dans celle-ci, notamment les séparateurs et l'identificateur de syntaxe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-validate-an-instance-against-its-schema"></a>Pour valider une instance par rapport à son schéma  
  
1.  Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Dans l'Explorateur de solutions, ajoutez au projet tous les schémas requis pour l'instance du message.  
  
    1.  Si vous validez un document informatisé unique sans en-tête d'échange et de groupe, ajoutez le schéma de document correspondant à ce document informatisé.  
  
    2.  Si vous validez un échange comprenant un seul document informatisé, ajoutez au projet le schéma du document informatisé, ainsi que le schéma de lot correspondant au type de codage utilisé pour le message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).  
  
        > [!NOTE]
        >  Le schéma de lot est requis pour valider l'enveloppe de l'instance. Si vous n'utilisez que le schéma du message, l'enveloppe n'est pas validée.  
  
    3.  Si vous validez un échange traité par lot comprenant plusieurs documents informatisés, ajoutez au projet le schéma de chaque groupe de documents informatisés de l'instance du message, ainsi que le schéma de lot correspondant au type de codage utilisé pour le message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).  
  
        > [!NOTE]
        >  Si vous avez personnalisé le schéma de service, vous devez inclure le schéma de service personnalisé dans le projet BizTalk, en complément du ou des schémas de document (informatisé) et, si nécessaire, le schéma de lot.  
  
        > [!NOTE]
        >  Il est inutile de créer le projet pour valider une instance.  
  
3.  Affichez la page des propriétés associée au schéma dans l'Explorateur de solutions en procédant comme suit :  
  
    1.  Si vous validez un document informatisé unique, cliquez sur le schéma de document pour ce jeu de transactions, puis cliquez sur **propriétés**.  
  
    2.  Si vous validez un échange avec un document informatisé unique ou un échange par lot avec plusieurs jeux de transactions, cliquez sur le schéma de lot (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd schéma), puis cliquez sur **depropriétés**.  
  
4.  Dans la fenêtre Propriétés pour le schéma, pour **nom d’Instance d’entrée** Entrez le nom et le chemin d’accès de l’instance de message que vous souhaitez valider, ou accédez au fichier, sélectionnez-le, puis cliquez sur **OK**.  
  
5.  Pour **Type valider l’entrée d’Instance**, entrez le type de fichier à valider : **natif** pour un fichier EDI ou **XML** pour un fichier XML.  
  
    > [!NOTE]
    >  La validation d'un échange conservé XML n'est pas prise en charge. Si vous sélectionnez XML pour le **Type valider l’entrée d’Instance** propriété lors de la validation d’un échange conservé, l’opération échoue et rien n’est renvoyé. Toutefois, si vous sélectionnez **natif** pour le **Type valider l’entrée d’Instance** lorsque vous validez un échange conservé, l’opération réussira.  
  
6.  Cliquez sur le schéma du message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd si la validation d’un échange avec un document informatisé unique ou un échange par lot), puis sur **valider l’Instance**.  
  
7.  Dans le **propriétés de l’Instance EDI** boîte de dialogue zone, procédez comme suit :  
  
    1.  Si l’instance doit utiliser un séparateur de répétition, sélectionnez **séparateur de répétition**.  
  
    2.  Si l’instance doit utiliser des délimiteurs de fin, sélectionnez **Oui** pour **utiliser les délimiteurs de fin**.  
  
    3.  Si l’instance doit utiliser un caractère autre que **base**, sélectionnez **étendue** ou **Unicode** dans **identificateur de syntaxe**.  
  
    4.  Cliquez sur **OK**.  
  
        > [!NOTE]
        >  Le **propriétés de l’Instance EDI** boîte de dialogue peut apparaître une deuxième fois, une fois que vous avez cliqué sur **OK**. Dans ce cas, cliquez sur **OK** à nouveau.  
  
        > [!NOTE]
        >  Le **propriétés de l’Instance EDI** boîte de dialogue contiendra les mêmes valeurs dans la dernière opération de validation de l’instance qui a été exécutée pour le même utilisateur connecté.  
  
8.  Vérifiez qu’il existe un message dans le **sortie** fenêtre, indiquant que l’opération a réussi.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)   
 [Génération d’une Instance (EDI)](../core/generating-an-instance-edi.md)