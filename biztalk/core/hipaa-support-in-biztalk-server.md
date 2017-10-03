---
title: Prise en charge HIPAA dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ad8c64-6375-4364-80ce-440db943c222
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c34dd17ed875c5927b7a10d8238ec7828ab96c79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-support-in-biztalk-server"></a>Prise en charge HIPAA dans BizTalk Server
Cette rubrique fournit une brève présentation de la loi HIPAA et de la manière dont [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] le prend en charge.  
  
## <a name="introduction-to-hipaa"></a>Présentation de HIPAA  
 La loi américaine HIPAA (Health Insurance Portability Accountability Act) de 1996 impose aux entités concernées d'appliquer des normes spécifiées dans le cadre de l'exécution de transactions électroniques (demandes de prise en charge, de remboursement, d'admissibilité, d'état d'une demande de prise en charge et réponses associées, etc.). Loi HIPAA est des plans de contrôle d’intégrité, les chambres de compensation et la plupart des fournisseurs de soins de santé.  
  
## <a name="hipaa-support-in-biztalk-server"></a>Prise en charge de la loi HIPAA dans BizTalk Server  
 Microsoft œuvre dans le but d'aider les prestataires de soins de santé et les organisations connexes à améliorer la délivrance et le financement des soins de santé. Microsoft a pour objectif de réduire les efforts et moyens engagés par ces organisations en vue de se conformer aux réglementations HIPAA.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide les organisations à créer des processus d'entreprise automatisés connectés et interopérables entre différents systèmes de santé. Les organisations concernées par la loi HIPAA peuvent utiliser les fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer, implémenter et intégrer des solutions de prise en charge des transactions conformes à la réglementation fédérale.  
  
Les fonctionnalités natives de [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] assurent la prise en charge de la loi HIPAA. Il ne s'agit pas d'un complément au produit, comme un adaptateur ou un accélérateur, mais d'un composant intégré au produit. [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]EDI inclut des composants et fonctionnalités qui sont requises pour les deux sont conformes avec les mandats HIPAA et à l’adoption de la réglementation HIPAA sous la forme d’un processus d’entreprise géré et mesuré.  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] prend en charge les versions 5010 et 4010 de la loi HIPAA.  
  
## <a name="hipaa-documentation-in-biztalk-server"></a>Documentation relative à la loi HIPAA dans BizTalk Server  
 X12 (normalisé par ANSI et principalement utilisé en Amérique du Nord) et EDIFACT (normalisé par les Nations-Unies et principalement utilisé hors des États-Unis) sont les principales normes EDI. HIPAA est une norme dérivée de X12. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit la prise en charge HIPAA dans le cadre de la X12 natif fonctionnalité EDI. Aussi, les références à la prise en charge X12 dans la documentation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appliquent également au traitement HIPAA, sauf mention explicite contraire.  
  
 Les sections suivantes du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] incluent des informations spécifiques sur la loi HIPAA.  
  
 **Bien démarrer**  
  
-   [Documents informatisés HIPAA](../core/hipaa-transaction-sets.md)  
  
 **Planification et Architecture**  
  
-   [Version de schéma de Document HIPAA 5010](../core/hipaa-document-schema-version-5010.md)  
  
-   [Annotations des champs déclencheurs HIPAA schéma](../core/hipaa-schema-trigger-field-annotations.md)  
  
-   [Fractionnement de sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md)  
  
 **Développement**  
  
-   [Modification des schémas EDI](../core/modifying-edi-schemas.md) 

- [Personnalisation des énumérations dans le schéma d’enveloppe](../core/customizing-enumerations-in-the-envelope-schema.md)

- [Configuration de la Validation de champ croisé](../core/configuring-cross-field-validation.md)

  
 **Dépannage**  
  
-   [Problèmes connus avec EDI de traitement de réception](../core/known-issues-with-edi-receive-processing.md)  
  
-   [Problèmes connus avec les outils XML utilisés avec les Solutions EDI](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)  
  
## <a name="more-information-about-hipaa"></a>Plus d’informations sur la loi HIPAA  
  
-   Pour plus d’informations sur l’American National Standards Institute, Accredited Standards Committee pour l’échange de données informatisé, accédez à [ASC X12 accueil](http://www.x12.org/).  
  
-   Pour plus d’informations sur le sous-comité d’assurance de X12 et leur implémentation repères adoptés dans le cadre de HIPAA, accédez à [Washington Publishing Company HIPAA EDI Guide](http://www.wpc-edi.com/).
  
-   Pour plus d’informations sur le groupe de travail pour l’échange de données informatisé, accédez à [Workgroup for Electronic Data Interchange page d’accueil](http://www.wedi.org/).