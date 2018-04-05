---
title: Composants | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, components
ms.assetid: 8793534f-5bd7-4cd3-9a42-8f0895f91007
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca9c5fdb04ffd182a8c51963c1a5c7cf5e7f8c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="components"></a>Components
Vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] composants afin d’implémenter des solutions intergiciel (middleware) orientée SWIFT qui facilitent la négociation de relations, intégration d’application d’entreprise (IAE) et application et automatisation des flux de travail d’entreprise partenaire. Ces composants sont les suivantes :  
  
-   **Schémas de Message SWIFT.** Vous utilisez le langage de définition de schéma XML (XSD)-composants de pipeline schémas conformes pour faciliter l’analyse des messages de fichier plat SWIFT natif en XML à l’aide de la SWIFT et [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] runtime. Après la conversion des données SWIFT en XML, vous utilisez un mappage pour le transformer en un autre format, telles que les fichiers plats délimités ou fichiers plats positionnels. Cette transformation vous permet d’utiliser ces fichiers dans vos applications existantes. Vous pouvez également utiliser les données XML sans aucun mappage, comme pour les scénarios de validation seule. Schémas SWIFT également appliquent des règles de format et les données définies par le SWIFT. Pour obtenir une liste complète des schémas fournis dans cette version, consultez [prise en charge des Messages](../../adapters-and-accelerators/accelerator-swift/supported-messages.md).  
  
-   **Les stratégies de Validation SWIFT et Framework.** Vous utilisez [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] stratégies du moteur de règles d’entreprise (BRE) pour valider et d’appliquer les règles de données, le format, réseau et d’utilisation définis par le SWIFT. Le désassembleur SWIFT et [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] composant de validation appeler le moteur BRE. Erreurs de validation sont rassemblés dans des objets de collection d’erreurs et messages erronés sont marqués avec des propriétés promues spéciales avant d’être publiée pour la base de données MessageBox.  
  
-   **Composants de Pipeline SWIFT.** Les composants désassembleur et assembleur de pipeline BizTalk vous permet de traiter les messages SWIFT. Le désassembleur SWIFT dynamiquement résout les types de messages SWIFT, Désassemble les lots de messages SWIFT, analyse les messages au format XML et valide les messages par rapport à des formats de données rapide et les règles de réseau et l’utilisation. L’assembleur SWIFT sérialise les données XML au format de fichier plat SWIFT.  
  
-   [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]  **Composant de validation.** Le [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] assembly fournit la classe interfaces de programmation (API) qui peuvent être utilisés dans les formes d’expression d’orchestration BizTalk. Ces classes fournissent les mêmes fonctionnalités de validation de messages SWIFT effectuée par le désassembleur SWIFT. Cette fonctionnalité permet d’avoir lieu dans les orchestrations (par exemple, après la transformation ou de modification d’un message SWIFT) de la validation de message.  
  
-   **Message Repair et New Submission.** Vous utilisez la fonctionnalité réparer du Message et de la nouvelle soumission de réparer les messages que la validation échoue ou que le désassembleur rapide ne peut pas analyser, ou pour créer et envoyer des nouveaux messages. Cette fonctionnalité est implémentée dans le processus d’orchestration MrsrRepair, site MRSR SharePoint, et [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
-   **FRR rapprochement de réponse.** Rapprochement de réponse FRR rapproche une réponse FIN avec le message envoyé à l’origine par A4SWIFT, l’activation de traitement personnalisé de l’ensemble de corrélations de réponse de message résultant. FRR est implémenté par l’orchestration FrrMain, le FRR emplacement de réception et ports d’envoi et l’adaptateur BizTalk pour MQSeries.  
  
-   **Kit de développement logiciel (SDK).** Le SDK fournit des outils, des didacticiels et exemples pour faciliter le développement et le déploiement de solutions BizTalk de base SWIFT. Ces solutions sont les suivantes :  
  
    -   [Didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-swift/end-to-end-tutorial2.md)  
  
    -   [Utilitaire de déploiement BRE](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)  
  
    -   [SWIFT schémas d’en-tête et code de fin](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   **Documentation.** [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]Aide décrit ce que vous devez planifier, développer, déployer et gérer vos solutions basée sur SWIFT de BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
[Runtime, la réparation de messages, la réponse FIN et la messagerie](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)