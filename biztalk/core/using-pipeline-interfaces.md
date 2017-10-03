---
title: "À l’aide des Interfaces de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb88d0d-23ab-4fdb-bcd2-56050456cf69
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c365a8d7bdf37564d3d9b2dceac1c8615e126ebc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-interfaces"></a>À l’aide des Interfaces de Pipeline
Un composant de pipeline est un composant .NET ou COM qui implémente un ensemble d'interfaces prédéfinies en vue d'interagir avec le moteur de messagerie BizTalk. Suivant la fonctionnalité du composant, différentes interfaces doivent être implémentées. Cette rubrique présente ces interfaces et certaines de leurs méthodes.  
  
> [!WARNING]
>  Si vous créez un composant de pipeline personnalisé avec COM, vous devez configurer votre composant de sorte qu'il utilise le modèle MTA (Multi-Threaded Apartment). Faute de quoi, l'appel de votre composant échouera avec une erreur E_NOINTERFACE.  
  
## <a name="ipipelinecontext"></a>IPipelineContext  
 Tous les composants de pipeline peuvent utiliser **IPipelineContext** méthodes pour accéder à tous les documents des interfaces de traitement. Le **IPipelineContext** interface fournit les fonctionnalités suivantes :  
  
-   Elle permet aux composants d'extraire les paramètres d'étape et de pipeline ambiants.  
  
-   Elle permet aux composants de récupérer les usines de messages et les messages. Grâce à ces usines, les composants peuvent créer divers objets nécessaires à leur exécution.  
  
-   Elle permet aux composants de récupérer les spécifications de document, à savoir un schéma XSD et des annotations.  
  
## <a name="ibasecomponent"></a>IBaseComponent  
 Cette interface est obligatoire pour tous les composants afin de fournir les informations de base les concernant.  
  
## <a name="icomponent"></a>IComponent  
 Cette interface est implémentée par tous les composants de pipeline, à l'exception des assembleurs et des désassembleurs, afin de récupérer des messages du moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en vue de leur traitement et de les retransmettre une fois traités au moteur.  
  
 **Exécutez.** méthode appelée par le moteur pour transmettre le message d'entrée au composant et récupérer le message traité depuis le composant.  
  
## <a name="ipropertybag-ipersistpropertybag"></a>IPropertyBag, IPersistPropertyBag  
 Composants de pipeline doivent implémenter **IPersistPropertyBag** pour recevoir ses informations de configuration. Cette interface et **IPropertyBag** sont des interfaces standard. Pour plus d'informations sur ces interfaces, reportez-vous à la documentation du kit de développement (SDK) Microsoft .NET Framework.  
  
## <a name="idisassemblercomponent"></a>IDisassemblerComponent  
 Un composant de désassemblage est un composant de pipeline qui reçoit un message en entrée et produit zéro ou plusieurs messages en sortie. Les composants de désassemblage sont utilisés pour fractionner des échanges de messages en documents individuels. Un composant désassembleur doit implémenter les méthodes de la **IDisassemblerComponent** interface récupère les messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le traitement et à passer désassemblé documents revenir [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
|Méthode| Description|  
|------------|-----------------|  
|**Désassembler**|Effectue le désassemblage du document entrant **pInMsg**.|  
|**GetNext**|Obtient le message suivant dans l'ensemble de messages résultant de l'exécution du désassembleur. Retourne **NULL** s’il n’existe plus aucun message.|  
  
 Si vous souhaitez écrire un composant de désassembleur qui prenne en charge le traitement des échanges récupérables, vous devez suivre les points suivants :  
  
1.  Rendez les flux d'entrée aptes à une recherche en les enveloppant dans un flux VirtualStream().  
  
2.  Dans GetNext(), créez une logique permettant de déterminer un message incorrect. Lorsqu'un message est incorrect, définissez BTS.MessageDestination = "SuspendQueue" et renvoyez le message dans GetNext().  
  
3.  Si le message est correct, définissez BTS.SuspendMessageOnRoutingFailure = True et renvoyez le message dans GetNext().  
  
## <a name="iassemblercomponent"></a>IAssemblerComponent  
 Un composant d'assemblage est un composant de pipeline qui reçoit plusieurs messages en entrée et produit un message en sortie. Les composants d’assemblage sont utilisés pour collecter des documents individuels dans le lot d'échange de messages.  
  
> [!NOTE]
>  Dans cette version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la fonctionnalité d'assemblage n'est pas utilisée, par conséquent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transmet toujours un document à la sortie de composant.  
  
 Un composant d’assembleur implémente les **IAssemblerComponent** méthodes sont appelées par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moteur au moment de l’exécution.  
  
|Méthode| Description|  
|------------|-----------------|  
|**AddDocument**|Ajoute le document **pInMsg** à la liste des messages qui seront inclus dans l’échange.|  
|**Assembler**|Construit l'échange à partir des messages ajoutés par la méthode précédente. Retourne un pointeur vers le message assemblé.|  
  
## <a name="iprobemessage"></a>IProbeMessage  
 Tout composant de pipeline (général, assemblage ou désassemblage) peut implémenter **IProbeMessage** s’il requiert la fonctionnalité de sondage des messages. Un composant de sonde est utilisé dans les étapes du pipeline qui ont **PremièreCorrespondance** mode d’exécution. Dans ces étapes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transmet le message au composant et le **sonde** méthode examine le début du message afin de déterminer si le composant reconnaît le format du message.  
  
|Méthode| Description|  
|------------|-----------------|  
|**Sonde**|Cette méthode prend **pInMsg** message et retourne **True** si le format est reconnu ou **False** dans le cas contraire.|  
  
## <a name="inameditem"></a>INamedItem  
 Il s'agit de l'interface d'aide permettant d'accéder aux schémas de document à partir du code géré et non géré.  
  
## <a name="inameditemlist"></a>INamedItemList  
 Il s'agit de l'interface d'aide permettant d'accéder aux schémas de document à partir du code géré et non géré.  
  
## <a name="idocumentspec"></a>IDocumentSpec  
 Composants de pipeline peuvent utiliser les méthodes de la **IDocumentSpec** de l’interface pour effectuer des actions spécifiques au document, tels que le déplacement des propriétés de contenu pour le contexte et vice-versa, l’accès à des schémas de document et ainsi de suite.  
  
|Méthode| Description|  
|------------|-----------------|  
|**Type de document**|Retourne le type du document actuel.|  
|**DocSpecName**|Retourne le nom de la spécification du document actuel.|  
|**GetSchemaCollection**|Retourne la liste des schémas du document actuel.|  
|**GetBodyPath**|Retourne le chemin XPath du nœud dans le document où débute le corps.|  
|**GetDistinguishedPropertyAnnotationEnumerator**|Retourne un énumérateur de dictionnaire de toutes les annotations de propriété de champ distinctif.|  
|**GetPropertyAnnotationEnumerator**|Retourne un énumérateur de toutes les annotations de propriété.|  
  
## <a name="icomponentui"></a>IComponentUI  
 Les composants de pipeline doivent implémenter cette interface afin d'être utilisés dans l'environnement du Concepteur de pipeline.  
  
|Méthode| Description|  
|------------|-----------------|  
|**Icône**|Fournit l'icône associée au composant.|  
|**Valider**|Le Concepteur de pipeline appelle cette méthode avant la compilation du pipeline afin de s'assurer que toutes les propriétés de configuration sont correctement définies.|  
  
 Le **icône** propriété retourne un **IntPtr**. L’exemple c# suivant montre comment retourner un **IntPtr**.  
  
```csharp  
static   ResourceManager resManager = new ResourceManager("ResourceManager", Assembly.GetExecutingAssembly());  
...  
[Browsable(false)]  
public IntPtr Icon  
{  
   get  
   {  
      return ((Bitmap)resManager.GetObject("MyIcon")).GetHicon();  
   }  
}  
```  
  
 Pour plus d’informations, consultez **Interface IComponentUI (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## <a name="see-also"></a>Voir aussi  
 [Développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md)   
 [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md)