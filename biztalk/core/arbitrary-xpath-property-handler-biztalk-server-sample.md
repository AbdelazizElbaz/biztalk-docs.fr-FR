---
title: "Le Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
ms.assetid: 4eb26c38-5ece-42b0-a28e-73214df1dc41
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f2f59ce48a3d46ebf33889e31a55f9aa452fd17
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="arbitrary-xpath-property-handler-biztalk-server-sample"></a>Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server)
Le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) illustre l'écriture d'un composant de pipeline personnalisé pour promouvoir des propriétés spécifiques sur un document XML envoyé à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez utiliser la fonctionnalité contenue dans l'exemple pour créer des composants Standard, Assembleur et Désassembleur personnalisés pour évaluer des expressions XPath.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple inclut un document XML de bon de commande à traiter, DocInstance.xml. L'exemple utilise les étapes suivantes pour traiter DocInstance.xml :  
  
1.  DocInstance.xml est récupéré par un port de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et traité par un composant de pipeline personnalisé nommé gestionnaire de propriété XPath arbitraire.  
  
2.  Le composant Gestionnaire de propriété XPath arbitraire promeut tous \<prix\> et \<quantité\> éléments avec une expression XPath arbitraire comme défini dans le schéma de bon de commande. L'expression XPath contient également la position construct à utiliser avec des éléments enfants ambigus de l'élément racine du document de bon de commande.  
  
3.  Le composant Gestionnaire de propriété XPath arbitraire détermine le type de message et le promeut dans le contexte du message.  
  
4.  Ensuite, le composant envoie le document XML avec les éléments promus à une orchestration pour un traitement supplémentaire.  
  
5.  L'orchestration accède aux éléments promus dans le document de bon de commande et calcule le nombre total d'articles du bon de commande.  
  
6.  L'orchestration crée un document de bon de commande contenant les informations du bon de commande d'origine ainsi que le total mis à jour.  
  
7.  Le nouveau document de bon de commande est écrit dans un fichier du répertoire \Output.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Samples Path\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|ArbitraryXPathPropertyHandler.sln|Fichier de solution du composant de pipeline personnalisé.|  
|ArbitraryXPathPropertyHandler.resX|Fichier de ressources.|  
|ArbitraryXPathPropertyHandlerComp.cs|Implémentation du composant principal.|  
|AssemblyInfo.cs|Informations de l'assembly.|  
|Cleanup.bat|Exemple de fichier de nettoyage.|  
|PromotingMap.cs|Promotion de propriétés comme implémentation du mappage des types CLR natifs.|  
|PropertyAttributes.cs|Attributs personnalisés, descripteur de propriété et implémentation d'ICustomTypePropertyDescriptor.|  
|SchemaMap.cs|Mappage de schéma à partir du type de message à IDocumentSpec pour résoudre l'ambiguïté de schéma.|  
|Setup.bat|Création et configuration de l'exemple de composant de pipeline.|  
|VirtualStream.cs|Implémentation du flux virtuel.|  
|SeekableReadOnlyStream.cs|Implémentation du flux en lecture seule et identifiable.|  
|ArbitraryXPathSample.sln|Exemple de fichier de solution de l'orchestration.|  
|CalculateTotalAmount.odx|Exemple d'orchestration.|  
|PODocument.xsd|Schéma de bon de commande.|  
|DocInstance.xml|Exemple d'instance de bon de commande.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Cet exemple est conçu pour s'exécuter dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] s'exécutant sur le même ordinateur. Si votre environnement ne correspond pas à cette configuration, vous devez modifier le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) pour qu'il pointe sur l'ordinateur SQL Server correct.  
  
> [!IMPORTANT]
>  Setup.bat suppose que votre répertoire d'installation de Microsoft Windows est C:\Windows. Si votre installation Windows se trouve dans un autre répertoire, vous devez modifier le fichier ArbitraryXPathPropertyHandler.csproj pour refléter l'emplacement de l'assembly Microsoft.BizTalk.Component.Utilities dans le GAC. Dans l’élément de référence, modifiez \<SYSTEMROOT\> à l’emplacement où Windows est installé (par exemple, C:\WINNT\\).  
  
```  
<Reference  
  Name = "Microsoft.BizTalk.Component.Utilities"  
  AssemblyName = "Microsoft.BizTalk.Component.Utilities"  
  HintPath = "<SYSTEMROOT>\assembly\GAC\Microsoft.BizTalk.Component.Utilities\3.0.1.0__31bf3856ad364e35\Microsoft.BizTalk.Component.Utilities.dll"  
/>  
```  
  
 Utilisez la procédure suivante pour créer et initialiser le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, remplacez les répertoires (**cd**) dans le dossier suivant :  
  
     *\<Samples Path\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   crée le composant de pipeline Gestionnaire de propriété XPath arbitraire ;  
  
    -   Composant de pipeline copies générés le  *\<chemin d’Installation\>*\Pipeline Components directory.  
  
    -   crée les ports d'envoi et de réception ;  
  
    -   crée les répertoires d'entrée et de sortie utilisés dans l'exemple ;  
  
    -   installe l'exemple d'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ArbitraryXPathSample ;  
  
    -   lie les ports à l'exemple d'orchestration ;  
  
    -   démarre l'orchestration.  
  
    > [!NOTE]
    >  Aucune erreur ne doit être signalée lors de la création et de l'initialisation. En cas d'erreur, veillez à ce que vous ayez tous les logiciels nécessaires installés et que les outils de création Microsoft sont disponibles dans le chemin d'accès.  
  
    > [!NOTE]
    >  Pour annuler les modifications apportées par Setup.bat, arrêtez puis redémarrez l'instance de l'hôte à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ensuite, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Copiez le fichier de bon de commande DocInstance.xml dans le répertoire \Input. Le fichier de bon de commande est récupéré par un port de réception qui envoie les données XML au composant de pipeline Gestionnaire de propriété XPath arbitraire.  
  
2.  Affichez le contenu dans le répertoire \Output. Notez la création d'un fichier contenant toutes les informations du fichier DocInstance.xml qui vous avez copié dans le répertoire \Input. La différence dans le fichier qui est désormais le \<TotalAmount\> élément a été rempli avec le montant total pour le bon de commande.  
  
## <a name="comments"></a>Commentaires  
 Les expressions XPath canoniques sont des expressions simples tels que «/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/\*[local-name()='element-name']/@\*[local-name='attribute name']».  
  
 Une expression XPath arbitraire peut être complexe, par exemple « //element-name//*[local-name()='element-name' and position()=2] ». En fait, vous obtenez une erreur d'exécution indiquant que les expressions XPath non canoniques ne sont pas prises en charge par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] si votre schéma a un XPath non canonique utilisé dans le corps XPath ou une propriété XPath. Une solution pour la prise en charge des expressions XPath arbitraires consiste à créer des composants Désassembleur et Assembleur personnalisés prenant en charge un corps XPath arbitraire ainsi que des expressions de propriété XPath arbitraire.  
  
 Cet exemple utilise la séquence d’étapes suivante dans le composant de pipeline personnalisé lorsque **IComponent.Execute** est implémenté :  
  
1.  Crée un flux virtuel identifiable sur le flux du corps du message entrant. (Comme le message entrant peut être volumineux et que le flux peut être non identifiable, il doit avoir un faible encombrement mémoire et être capable de modifier les positions de flux.)  
  
2.  Crée un message sortant et un corps, attribue un flux virtuel au nouveau corps, clone les propriétés du corps ainsi que le contexte de message.  
  
3.  Obtient un schéma pour le message entrant ou basé sur les schémas spécifiés au moment de la conception.  
  
4.  Charge le flux de données dans une instance de **System.Xml.XmlDocument**.  
  
5.  Passe en revue les propriétés promues et les champs distinctifs et les promeut ou les écrit dans le contexte de message du message sortant.  
  
6.  Renvoie le message sortant.  
  
7.  Écrit le message sortant dans un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)