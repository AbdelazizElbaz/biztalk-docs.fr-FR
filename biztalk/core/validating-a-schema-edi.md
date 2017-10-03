---
title: "Validation d’un schéma (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6175460-2dcf-4fef-b770-02f0a058bf93
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cd2672f7ba9be796c1ff802be51324fbfe3256
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-schema-edi"></a>Validation d'un schéma (EDI)
Vous pouvez valider un schéma EDI pendant la phase de conception. Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. L'opération de validation du schéma consiste à valider un schéma selon des règles EDI. Il est inutile de désigner une instance de message entrant pour valider un schéma.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-validate-a-schema"></a>Pour valider un schéma  
  
1.  Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Dans l'Explorateur de solutions, ajoutez au projet le schéma du message que vous souhaitez valider.  
  
    > [!NOTE]
    >  Ces derniers se trouvent dans le sous-dossier approprié, sous le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI. Pour plus d’informations sur l’installation des fichiers de schéma, consultez [comment installer les fichiers de schéma EDI](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).  
  
    > [!NOTE]
    >  Il est inutile de générer un projet pour valider un schéma.  
  
2.  Cliquez sur le schéma dans l’Explorateur de solutions, puis cliquez sur **valider le schéma**.  
  
3.  Vérifiez qu'il y a un message dans la fenêtre Sortie indiquant que l'opération a réussi.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)