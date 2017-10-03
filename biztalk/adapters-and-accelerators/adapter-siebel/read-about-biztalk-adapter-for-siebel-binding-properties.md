---
title: "En savoir plus sur l’adaptateur BizTalk pour Siebel, propriétés de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding properties, setting
- binding properties, adapter
- how to, set binding properties
ms.assetid: 48c77a2d-091c-40e0-aaf3-dc2ec34c55f2
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3237be098ea19fc7ff35770ddcb38a10d1e85c1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="read-about-biztalk-adapter-for-siebel-binding-properties"></a>En savoir plus sur l’adaptateur BizTalk pour Siebel, propriétés de liaison
Le [!INCLUDE[adaptersiebel_md](../../includes/adaptersiebel-md.md)] expose plusieurs propriétés de liaison qui vous permettent de contrôler son comportement au moment du design et d’exécution. Cette section décrit ces propriétés de liaison et fournit des liens vers des rubriques qui expliquent comment vous pouvez les définir.  
  
## <a name="the-siebel-adapter-binding-properties"></a>Les propriétés de liaison de l’adaptateur Siebel  
 Le tableau suivant présente les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] propriétés de liaison groupées par catégorie. La catégorie fait référence au nœud sous lequel chaque propriété de liaison s’affiche dans les boîtes de dialogue qui sont présentés par différentes applications pour configurer l’adaptateur (ou la liaison).  
  
|Propriété de liaison|Catégorie| Description|Type .NET|  
|----------------------|--------------|-----------------|---------------|  
|EnableBizTalkCompatibilityMode|Général|Spécifie si l’élément de liaison BizTalk en couche canal doit être chargé.<br /><br /> Affectez la valeur **True** pour charger l’élément de liaison. Sinon, affectez la valeur **False**.<br /><br /> Lorsque vous utilisez les cartes [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la propriété **True**. Lorsque vous utilisez les cartes [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez toujours définir la propriété **False**.|bool (System.Boolean)|  
|Nom|Général|Spécifie le nom du fichier généré par le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour contenir la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] constitue le nom de fichier en ajoutant « Client » à la valeur de la **nom** propriété la valeur par défaut est « SiebelBinding » ; pour cette valeur, le fichier généré est nommé « SiebelBindingClient ».|chaîne|  
|CloseTimeout|Général|Spécifie le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] délai de fermeture de la connexion. La valeur par défaut est de 1 minute.|System.DateTime|  
|OpenTimeout|Général|Spécifie le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] délai d’ouverture de connexion. La valeur par défaut est de 1 minute.|System.DateTime|  
|ReceiveTimeout|Général|Spécifie le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] délai de réception du message. La valeur par défaut est 10 minutes.|System.DateTime|  
|SendTimeout|Général|Spécifie le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] délai d’envoi de message. La valeur par défaut est de 1 minute.|System.DateTime|  
|EnableConnectionPooling|Connexion|Spécifie si le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pool de connexions est activé. La valeur par défaut est **true**, qui spécifie que le pool de connexions est activé.|bool (System.Boolean)|  
|IdleConnectionTimeout|Connexion|Spécifie le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] délai de connexion inactive. Lorsqu’une connexion est inactive pendant une période qui dépasse ce délai d’attente, la connexion sera supprimée. La valeur par défaut est de 1 minute.|System.DateTime|  
|MaxConnectionsPerSystem|Connexion|Spécifie le nombre maximal de connexions dans le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pool de connexions. La valeur par défaut est 5. **MaxConnectionsPerSystem** est une propriété statique dans un domaine d’application. Cela signifie que lorsque vous modifiez **MaxConnectionsPerSystem** pour l’instance d’une liaison dans un domaine d’application, la nouvelle valeur s’applique à tous les objets créés à partir de toutes les instances de liaison au sein de ce domaine d’application.|int (System.Int32)|  
|EnablePerformanceCounters|Diagnostics|Spécifie si le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] les compteurs de performance et la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] compteur des performances de latence de LOB sont activés. La valeur par défaut est **true**; les compteurs de performance sont activés. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] compteur de performance de latence de LOB mesure le temps total l’adaptateur passe à effectuer des appels au système Siebel.|bool (System.Boolean)|  
|Transactionsrestauration|Diagnostics|Spécifie s’il faut capturer des données d’entreprise dans les traces. La valeur par défaut est **false**; données de l’entreprise ne sont pas capturées.|bool (System.Boolean)|  
|AcceptCredentialsInUri|Ne pas signalées par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].|Spécifie si l’URI de connexion Siebel peut contenir des informations d’identification de l’utilisateur pour le système Siebel. La valeur par défaut est **false**, ce qui désactive les informations d’identification de l’utilisateur dans l’URI de connexion. Si **AcceptCredentialsInUri** est **false** et l’URI de connexion contient des informations d’identification de l’utilisateur, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] lève une exception. Vous pouvez définir **AcceptCredentialsInUri** à **true** si vous devez spécifier les informations d’identification dans l’URI. Pour plus d’informations, consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).|bool (System.Boolean)|  
  
## <a name="how-do-i-set-siebel-binding-properties"></a>Comment définir les propriétés de liaison de Siebel ?  
 Vous pouvez définir les propriétés de liaison de Siebel lorsque vous configurez une connexion à un système Siebel. Pour plus d’informations sur la définition des propriétés de liaison lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut est null, cette propriété de liaison ne sera pas disponible dans le fichier de liaison (un fichier XML) ou le fichier app.config respectivement. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier de liaison ou le fichier app.config, si nécessaire.  
  
-   Configurer un port d’envoi ou de réception du port (emplacement) dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).
  
-   Utilisez le modèle de canal WCF dans une solution de programmation, consultez [créer un canal à l’aide de Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).  
  
-   Utilisez le modèle de service WCF dans une solution de programmation, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  
  
-   Utilisez WCF Service Model Metadata Utility Tool (svcutil.exe), voir [à l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)