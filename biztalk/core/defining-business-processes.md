---
title: "Définition des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5e0fdfe-e298-4f32-a7c5-d081b926a206
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6776b78b06e68b67e9391d4f3fb1ddf64db72198
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-business-processes"></a>Définition des processus d’entreprise
L'échange de messages entre différents systèmes fait nécessairement partie de la résolution des problèmes par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'objectif réel, cependant, est de définir et d'exécuter des processus d'entreprise basés sur les applications. Le moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise des orchestrations pour définir la logique de ces processus d'entreprise. Pour créer et évaluer des groupes de règles d'entreprise, il utilise le Moteur de règles d'entreprise. Cette section décrit les orchestrations et le Moteur de règles d'entreprise.  
  
## <a name="using-orchestrations"></a>Utilisation des orchestrations  
 La logique d'un processus d'entreprise automatisé peut être implémentée directement dans un langage, tel que Microsoft Visual Basic ou Microsoft Visual C#. Toutefois, créer, maintenir et gérer des processus d'entreprise complexes dans des langages de programmation classiques peuvent être difficiles. Contrairement à ses prédécesseurs, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adopte une approche différente. Il permet aux gestionnaires des activités ou aux développeurs de définir un processus d'entreprise sous forme graphique. Cela peut s'avérer plus rapide que la création du processus directement dans un langage de programmation, tout en rendant le processus plus simple à comprendre, expliquer et modifier. Les processus d'entreprise créés de cette manière peuvent également être surveillés plus facilement et ce fait est exploité par la technologie BAM (Business Activity Monitoring).  
  
 Pour un développeur, la création d’une orchestration repose sur trois outils principaux : l’Éditeur BizTalk pour la création de schémas XML, le Mappeur BizTalk pour définir des conversions entre ces schémas et le Concepteur d’Orchestration pour spécifier la logique d’entreprise processus. Tous ces outils sont hébergés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], offrant aux développeurs un environnement cohérent. Cette section décrit ce que fait chacun de ces outils et comment ils fonctionnent ensemble.  
  
### <a name="creating-schemas-the-biztalk-editor"></a>Création de schémas : L’Éditeur BizTalk  
 Les orchestrations fonctionnent avec des documents XML, chacun d'eux étant conforme à un certain schéma XML. L'Éditeur BizTalk permet aux développeurs de définir ces schémas, lesquels définissent essentiellement la structure et les types d'informations d'un document, à l'aide du langage XSD (XML Schema Definition language).  
  
 La création de schémas XSD bruts, sans aucune prise en charge par des outils, n'est pas simple. Afin de rendre cette étape nécessaire plus abordable, l'Éditeur BizTalk permet aux utilisateurs (probablement aux développeurs) de créer un schéma en définissant ses éléments dans une hiérarchie graphique. Des schémas existants peuvent également être importés à partir de fichiers ou de services Web accessibles. Quelle que soit leur méthode d'acquisition, les schémas sont utilisés comme base pour les mappages BizTalk.  
  
### <a name="mapping-between-schemas-the-biztalk-mapper"></a>Le mappage entre les schémas : Le Mappeur BizTalk  
 Une orchestration implémentant un processus d'entreprise reçoit généralement des documents et en envoie d'autres. Souvent, une partie des informations des documents reçus est transférée aux documents envoyés, peut-être plus ou moins transformée. Par exemple, un processus d'exécution de commandes peut recevoir une commande pour un certain nombre d'articles, puis renvoyer un message indiquant que la commande a été refusée pour une certaine raison. Les informations présentes dans la commande, telles qu'un identificateur de demande et la quantité commandée, peuvent être copiées, à partir des champs inclus dans le message de commande reçu, dans des champs du message de rejet. Le Mappeur BizTalk peut être utilisé pour définir une transformation, appelée mappage, d'un document à l'autre.  
  
 ![Le mappage entre les schémas](../core/media/understandingbts-2010-mapper.gif "UnderstandingBTS_2010_Mapper")  
  
 Comme l'illustre la figure ci-avant, chaque mappage est exprimé par une corrélation graphique entre deux schémas XML, qui définit une relation entre les éléments de ces schémas. Le World Wide Web Consortium (W3C) a défini le language XSLT (Extensible Stylesheet Language Transformation) comme mode standard d'expression de ces types de transformations entre des schémas XML. Ainsi, des mappages dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont implémentés en tant que transformations XSLT.  
  
 La transformation définie dans un mappage peut être simple, telle que la copie de valeurs inchangées d'un document dans un autre. De telles copies de données directes sont exprimées à l'aide d'un lien, affiché dans le Mappeur BizTalk sous la forme d'une ligne reliant les éléments appropriés dans le schéma source à leurs équivalents dans le schéma de destination. Des transformations plus complexes sont également possibles à l'aide de fonctoids. Un fonctoid est un bloc de code exécutable qui peut définir arbitrairement des mappages complexes entre des schémas XML et, comme indiqué ci-avant, le Mappeur BizTalk le représente comme une case sur la ligne reliant les éléments en cours de transformation. Comme certaines de ces transformations sont relativement courantes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compte un certain nombre de fonctoids intégrés. Ces fonctoids intégrés sont regroupés en catégories, qui sont les suivantes :  
  
-   Fonctoids mathématiques qui réalisent des opérations telles que l'addition, la multiplication et la division des valeurs des champs du document source et le stockage du résultat dans un champ du document cible.  
  
-   Fonctoids de conversion qui convertissent une valeur numérique en son équivalent ASCII et inversement.  
  
-   Fonctoids logiques pouvant servir à déterminer si un élément ou un attribut doit être créé dans le document cible en fonction d'une comparaison logique entre des valeurs spécifiées dans le document source. Ces valeurs peuvent être comparées, entre autres, en termes d'égalité, de supériorité, d'infériorité.  
  
-   Fonctoids cumulés qui calculent des moyennes, des sommes ou d'autres valeurs à partir de divers champs du document source, puis stockent le résultat dans un champ unique du document cible.  
  
-   Fonctoids de base de données qui peuvent accéder aux informations stockées dans une base de données.  
  
 Il est également possible de créer des fonctoids personnalisés directement dans XSLT ou à l'aide de langages compatibles .NET tels que Visual C# et Visual Basic. Des fonctoids peuvent aussi être combinés dans des séquences, en mettant en cascade la sortie de l'une dans l'entrée de l'autre.  
  
 Il est essentiel que vous puissiez définir le schéma XML d'un document, ainsi qu'un mécanisme de mappage d'informations entre des documents ayant des schémas différents. L'Éditeur BizTalk et le Mappeur BizTalk résolvent ces deux problèmes. Toutefois, la définition des schémas et des mappages ne représente qu'une partie du processus. Vous devez également spécifier la logique d'entreprise qui utilise les schémas et appelle les mappages.  
  
### <a name="defining-business-logic-the-orchestration-designer"></a>Une définition de logique métier : Le Concepteur d’Orchestration  
 Un processus d'entreprise est un ensemble d'actions qui, ensemble, répondent à certains besoins utiles de l'entreprise. Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un développeur peut utiliser le Concepteur d'Orchestration pour définir graphiquement ces actions. Au lieu d'exprimer les étapes dans un langage de programmation, un développeur peut créer une orchestration en reliant logiquement une série de formes. Les formes disponibles dans le Concepteur d'Orchestration incluent :  
  
-   La forme Réception, qui permet à l'orchestration de recevoir des messages. Une forme Réception peut disposer d'un filtre qui définit les types de messages à recevoir. Elle peut aussi être configurée pour commencer une nouvelle instance d'une orchestration à l'arrivée d'un nouveau message.  
  
-   La forme Envoi, qui permet à l'orchestration d'envoyer des messages.  
  
-   La forme Port, qui définit la manière dont les messages sont transmis. Chaque instance d'une forme Port est connectée à une forme Envoi ou Réception. Chaque port dispose également d'un type, qui définit notamment le genre de messages que le port peut recevoir ; une direction, telle que l'envoi ou la réception ; une liaison, qui détermine comment un message est envoyé ou reçu, par exemple, en spécifiant une URL particulière ou d'autres informations.  
  
-   La forme Décider, qui représente une instruction « if-then-else » qui permet à une orchestration d'effectuer différentes tâches basées sur des conditions booléennes. Un Éditeur d'expression, inclus dans le Concepteur d'Orchestration, peut être utilisé pour spécifier cette instruction conditionnelle.  
  
-   La forme Boucle, qui contrôle la réalisation répétée d'une action tant qu'une certaine condition est vraie.  
  
-   La forme Construire un message, qui permet de créer un message.  
  
-   La forme Transformer, qui permet le transfert d'informations d'un document à l'autre, en les transformant grâce à l'appel des mappages définis avec le Mappeur BizTalk.  
  
-   La forme Actions parallèles, qui permet à un développeur de spécifier que des opérations multiples doivent être effectuées de façon parallèle plutôt que séquentielle. La forme qui suit cette forme n'est pas exécutée tant que toutes les actions parallèles ne sont pas terminées.  
  
-   La forme Étendue, qui permet le regroupement d'opérations en transactions et la définition de gestionnaires d'exceptions pour la gestion des erreurs. Les transactions atomiques traditionnelles et les transactions longues sont prises en charge. Contrairement aux transactions atomiques, les transactions longues s'appuient sur la logique de compensation plutôt que sur l'annulation pour gérer les événements inattendus.  
  
-   La forme Assignation du message, qui permet d'attribuer des valeurs aux variables d'orchestration. Ces variables peuvent être utilisées pour stocker des informations d'état utilisées par l'orchestration, telles qu'un message en cours de création ou une chaîne de caractères.  
  
 La figure suivante montre une orchestration créée dans le Concepteur d'Orchestration à l'aide de quelques-unes de ces formes. Dans cet exemple simple, un message est reçu, une décision est prise en fonction du contenu de ce message et l'un des deux chemins est exécuté comme résultat de cette décision. Les orchestrations qui résolvent de réels problèmes peuvent être bien plus complexes que celle-ci. Pour faciliter le travail avec des diagrammes plus complexes, le Concepteur d'Orchestration inclut une fonction de zoom avant et arrière. Les développeurs peuvent afficher uniquement les parties d'une orchestration qui les intéressent.  
  
 ![](../core/media/understandingbts-08-orchestration.gif "UnderstandingBTS_08_Orchestration")  
  
 Une fois qu'un développeur a défini une orchestration, le groupe de formes et de leurs relations est converti en langage MSIL (Microsoft Intermediate Language) utilisé par le Common Language Runtime (CLR) de .NET Framework. Finalement, le groupe de formes défini par un développeur BizTalk Server devient simplement un assembly .NET standard. Vous pouvez également ajouter un code explicite à une orchestration, si nécessaire, en appelant un objet COM ou .NET depuis une forme.  
  
### <a name="the-role-of-web-services"></a>Rôle des services Web  
 Les services Web permettent aux applications d'échanger des documents XML à l'aide de SOAP. Ils ont eu un impact considérable sur les plateformes d'intégration. Pour accéder à un service Web externe, un créateur d'orchestration peut utiliser l'option Ajouter une référence Web dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ainsi que l'adaptateur de services Web, pour appeler directement des opérations. De même, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] offre un Assistant Publication de services Web qui peut générer un projet de service Web ASP.NET exposant une ou plusieurs opérations d'une orchestration comme services Web pouvant être appelés par SOAP. Ces deux options permettent aux développeurs d'accéder à des services Web existants depuis un processus d'entreprise et d'exposer la fonctionnalité d'une orchestration en tant que service Web à d'autres processus d'entreprise.  
  
-   L'essor des services Web a également un impact sur la définition des processus d'entreprise. Par exemple, imaginez deux organisations qui interagissent à l'aide des services Web. Pour une interopérabilité efficace, il peut être nécessaire que chaque tiers de l'interaction connaisse le processus d'entreprise que l'autre utilise. Si les deux organisations utilisent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cela ne pose pas un gros problème car des outils, tels que la technologie de gestion des partenaires commerciaux (TPM), peuvent servir à communiquer cette information. Mais que se passe-t-il si elles utilisent des produits différents ? Dans des cas comme celui-ci, il est utile de pouvoir décrire les aspects des processus d'entreprise de manière non spécifique au fournisseur.  
  
 Pour cela, Microsoft, IBM et d'autres ont créé le langage BPEL (Business Process Execution Language). Un processus d'entreprise défini à l'aide du Concepteur d'Orchestration peut être exporté en BPEL et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut également importer des processus définis en BPEL. Si le langage est utile pour décrire et partager les parties d'un processus d'entreprise visibles de l'extérieur, BPEL se concentre davantage sur la résolution de ce problème que sur l'exécution multiplateforme de processus d'entreprise complets. Il est également important de comprendre que BPEL est entièrement créé sur les services Web, tandis que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et d'autres produits prenant en charge ce langage sont plus développés. Par exemple, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge le mappage entre différents schémas XML, en appelant des méthodes dans des objets locaux, et d'autres fonctionnalités qui ne sont pas disponibles dans BPEL. Pour toutes ces raisons et d'autres encore, BPEL n'est pas un langage complet de définition de processus d'entreprise. Comme BPEL est toujours en cours de normalisation par OASIS (Organization for the Advancement of Structured Information Standards), il est difficile de la considérer aujourd'hui comme une technologie aboutie.  
  
-   Les orchestrations sont le mécanisme fondamental de création de processus d'entreprise dans BizTalk Server. Certains aspects d'une orchestration ont tendance à changer plus souvent que d'autres, cependant. Notamment, les décisions incorporées dans un processus d'entreprise (les règles d'entreprise) sont typiquement son aspect le plus instable. Le plafond des dépenses d'une gestionnaire était de 100 000 $ la semaine dernière mais est passé à 500 000 $ en raison de sa promotion ou la commande maximale autorisée pour un client qui tarde à payer passe de 100 unités à seulement 10. Vous pouvez spécifier et mettre à jour ces règles à l'aide du Moteur de règles d'entreprise.  
  
## <a name="using-the-business-rule-engine"></a>Utilisation du Moteur de règles d'entreprise  
 Le Concepteur d'Orchestration, l'Éditeur BizTalk et le Mappeur BizTalk offrent une manière efficace de définir un processus d'entreprise et les règles qu'il utilise. Il peut être utile, cependant, de pouvoir définir et modifier facilement les règles d'entreprise. Pour cela, BizTalk Server fournit le Moteur de règles d'entreprise (BRE). Le plus souvent, les développeurs utilisent ce moteur tandis que les utilisateurs plus orientés sur les activités peuvent créer et modifier des ensembles de règles d'entreprise à l'aide d'un outil appelé Éditeur des règles d'entreprise.  
  
 Le Moteur de règles d'entreprise est particulièrement utile en cas d'évaluation d'un ensemble complexe de règles d'entreprise. La décision d'accorder un prêt, par exemple, peut s'appuyer sur un vaste ensemble de règles basées sur l'historique de crédit du client, son revenu et d'autres facteurs. De même, décider de vendre une assurance vie à un candidat dépend d'un certain nombre de paramètres, tels que son âge, son sexe et son état de santé. Il serait possible d'exprimer toutes ces règles sous forme d'instructions conditionnelles, à l'aide d'une forme Décider d'une orchestration, par exemple, mais cela serait relativement compliqué à implémenter. Pour des processus qui impliquent de nombreuses règles comme celui-ci, le Moteur de règles d'entreprise peut simplifier la vie d'un développeur.  
  
 À l'aide du Moteur de règles d'entreprise, les développeurs peuvent rapidement et facilement modifier les règles selon leurs besoins. Pour comprendre l'intérêt, imaginez les étapes nécessaires à la modification d'une règle d'entreprise implémentée dans une orchestration. Un développeur doit d'abord ouvrir l'orchestration dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], modifier les formes appropriées (et peut-être les objets .NET ou COM qu'elles appellent), puis créer et déployer l'assembly modifié. Cette opération nécessite également l'arrêt et le redémarrage de l'application BizTalk qui inclut cette orchestration. Si, au contraire, cette règle d'entreprise est implémentée à l'aide du Moteur de règles d'entreprise, elle peut être modifiée sans nouvelle compilation ni redémarrage. Tout ce qu'il faut faire, c'est utiliser l'Éditeur des règles d'entreprise pour modifier la règle souhaitée, puis redéployer le nouvel ensemble de règles. La modification prend effet immédiatement. Tandis que les orchestrations sont généralement créées et maintenues par des développeurs, les règles d'entreprise sont suffisamment lisibles pour que, dans certains cas, elles puissent être modifiées par des analystes d'entreprise qui n'ont pas besoin d'impliquer de personnel technique.  
  
 Le créateur d'un ensemble de règles d'entreprise commence généralement par utiliser l'Éditeur des règles d'entreprise pour définir un vocabulaire à utiliser pour spécifier ces règles. Chaque terme du vocabulaire fournit un nom convivial pour certaines informations. Par exemple, un vocabulaire peut définir des termes tels que Nombre livré, Quantité maximale d'articles ou Limite d'approbation. Chacun de ces termes peut être défini sur une constante ou être mappé à un élément ou attribut particulier dans un certain schéma XML (donc dans un message entrant) ou au résultat d'une requête SQL sur une certaine base de données, voire à une valeur d'un objet .NET.  
  
 Une fois le vocabulaire défini, l'Éditeur des règles d'entreprise peut être utilisé pour créer des stratégies d'entreprise qui utilisent ce vocabulaire. Chaque stratégie peut contenir une ou plusieurs règles d'entreprise. Une règle utilise les termes définis dans le vocabulaire, ainsi que des opérateurs logiques tels que Supérieur à, Inférieur à, Égal à et d'autres, pour définir comment un processus d'entreprise opère. Une règle d'entreprise peut définir comment des valeurs contenues dans un document XML reçu doivent affecter les valeurs créées dans un document XML envoyé, ou comment ces valeurs reçues doivent affecter la valeur écrite dans une base de données, etc.  
  
 Pour exécuter une stratégie d'entreprise, une orchestration utilise une forme RèglesAppel. Cette forme crée une instance du Moteur de règles d'entreprise, spécifie la stratégie à exécuter, puis transmet les informations requises par cette stratégie, telles qu'un document XML reçu. Le Moteur de règles d'entreprise peut également être appelé par programme, à l'aide d'un modèle d'objet .NET, ce qui lui permet d'être appelé à partir d'applications qui n'utilisent pas [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela signifie que les applications Windows Forms, les logiciels exposant des services Web et tout autre élément basé sur .NET Framework, peut utiliser le Moteur de règles d'entreprise pour aider à résoudre un problème.  
  
 Les vocabulaires et les règles d'entreprise peuvent être bien plus complexes (et bien plus puissants) que les exemples simples décrits ici. Mais l'idée fondamentale de définition d'un vocabulaire, puis d'ensembles de règles qui utilisent ce vocabulaire, est au cœur du Moteur de règles d'entreprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie BizTalk Server](../core/the-biztalk-server-messaging-engine.md)