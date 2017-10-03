---
title: "Découverte de Type dynamique des messages et la résolution de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic schema resolution
- disassembler, code sample
- schemas, dynamic resolution
- assembler, message types
- disassembler, message types
- code samples, disassembler
ms.assetid: 5f71d3df-a37e-4ef2-9055-b614656203e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77e9a8949787fcd3c7e942c406c9f31470894a8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-message-type-discovery-and-schema-resolution"></a>Découverte de Type dynamique des messages et la résolution de schéma
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] permet la résolution de découverte et le schéma de type dans l’assembleur et désassembleur SWIFT message dynamique.  
  
## <a name="swift-disassembler"></a>Désassembleur SWIFT  
 Le désassembleur SWIFT (DASM) a la possibilité de détecter le type de message d’un message reçu dynamiquement et de charger le schéma approprié nécessaire pour analyser le message. Le principal avantage de cette fonctionnalité est que vous pouvez configurer un seul pipeline à l’aide du désassembleur SWIFT pour traiter les messages SWIFT de n’importe quel type de messages SWIFT. Contrairement au désassembleur de fichier plat BizTalk natif, le désassembleur SWIFT ne nécessite pas que vous générez un pipeline de réception distincts pour chaque type de message que A4SWIFT pouvez rencontrer.  
  
 Vous pouvez utiliser la découverte de type dynamique message si vous supposez que, dans la plupart des cas, tous les messages qui reçoit d’un système commence par les données d’en-tête structurellement homogène. Dans l’en-tête de données sont des champs qui révèlent le type de message du message. Pour les messages SWIFT, les données d’en-tête se comprennent de blocs de messages SWIFT 1, 2 et 3, avec les informations de type de message contenues dans le bloc 2 (appelée de l’en-tête de l’Application).  
  
 Le composant de SWIFT DASM peut traiter toutes les « unique » (non-batch) SWIFT Messages à partir de la zone de sans nécessiter de toutes les propriétés à définir. Par défaut, le schéma de l’échange de SWIFT et le schéma d’en-tête de SWIFT ne sont pas définis ; Toutefois, le composant SWIFT DASM utilisera le schéma d’en-tête de SWIFT présent dans Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll pour détecter le Type de Message SWIFT dynamiquement et traiter les messages. En outre, BRE et la Validation XML sont activées par défaut afin de n’importe quel message traité doit être complètement validée. Définition de la propriété de schéma SWIFT en-tête pour pointer vers l’en-tête SWIFT dans RuntimeSchemas.dll également entraîne le même comportement que ci-dessus.  
  
 Lorsque la propriété de configuration de schéma d’en-tête SWIFT pour le désassembleur SWIFT est la valeur « None » (la valeur par défaut), le désassembleur résout dynamiquement et charge le schéma approprié en effectuant les étapes suivantes :  
  
1.  Utilise le schéma d’en-tête spécifié par l’utilisateur (spécifié par la propriété de configuration du schéma d’en-tête SWIFT) pour analyser le début (en-tête) du message de réception.  
  
2.  Inspecte l’en-tête qui en résulte « XML » pour le champ de propriété promue A4SWIFT_MessageType. Si ce champ existe, il utilise la valeur du champ en tant que le « type de message » et se poursuit à l’étape 4. Si le champ n’existe pas, il se poursuit à l’étape 3.  
  
3.  Inspecte l’en-tête XML pour le champ de propriété promue A4SWIFT_MessageType2 (attendu si le désassembleur ne trouve pas le champ A4SWIFT_MessageType). Utilise la valeur du champ A4SWIFT_MessageType2 comme le « type de message ».  
  
4.  Si le « type de message « identifié dans l’étape 2 ou 3 est « 574 », le désassembleur SWIFT vérifie si le type de message « 574 » est dans la liste des types de messages spécifiés dans la propriété de configuration de liste de messages de Type double (qui est une propriété du désassembleur). Si Oui, il se poursuit à l’étape 5. Si non, se poursuit à l’étape 6.  
  
5.  Inspecte l’en-tête XML pour le champ de propriété promue A4SWIFT_SecondaryMessageType. Si ce champ existe, le désassembleur utilise la valeur du champ (par exemple, « IRSLST ») en tant que le « message sous-type » et l’ajoute à la « type de message », par exemple, « 574_IRSLST ».  
  
    > [!IMPORTANT]
    >  L’explication donnée de l’étape 5 est une version simplifiée de ce que le désassembleur SWIFT réellement fait pour évaluer le sous-type du message. En réalité, le désassembleur SWIFT utilise l’algorithme suivant pour déterminer si un type de message a des sous-types et dans ce cas, ce que sous-types est la suivante.  
  
    ```  
    Given MT type number nxx ...  
    if nxx is in the Dual-Type list {  
      if field 119 exists AND field 119 is NOT null/empty {  
        if n == 1 {  
          if field 119 == "STP" {  
            Use MTnxxPLUS schema  
          } else if field 119 == "REMIT" {  
            Use MTnxx schema  
          } else {  
            Use MTnxx_<field 119> schema  
          }   
        } else {  
          // n != 1  
          Use MTnxx_<field 119> schema  
        }  
      } else {  
        // field 119 does not exist or 119 does exist but is null/empty  
        Use MTnxx schema  
      }  
    } else {  
      // nxx is not a dual-type message  
      Use MTnxx schema  
    }  
    ```  
  
6.  Le désassembleur connaît désormais le type de message, et il peut former le nom de schéma d’échange en concaténant des préfixes et suffixes (par exemple, « MT » dans le préfixe pour rendre « MT574_IRSLST ») de nommage de schéma fixe.  
  
7.  Charge le schéma de l’échange (par nom) et analyse le message entier, **à partir du début**, en utilisant le schéma chargé (cela signifie que le désassembleur analyse les données d’en-tête à deux reprises : une fois en utilisant le schéma d’en-tête et à l’aide de début du schéma d’échange). Le schéma d’échange doit être en mesure d’analyser le message entier, y compris l’en-tête.  
  
    > [!NOTE]
    >  Le désassembleur peut utiliser tous les schémas de message SWIFT d’A4SWIFT pour analyser l’ensemble de l’échange rapide (SWIFT blocs 1, 2, 3, 4 et 5). Le désassembleur utilise le schéma d’en-tête SWIFT par défaut pour analyser les blocs 1, 2 et 3 uniquement. Voir ci-dessous pour plus de détails.  
  
 L’algorithme de résolution de schéma décrit ci-dessus implique que pour la découverte de type de message dynamique fonctionne, le schéma d’en-tête SWIFT doit contenir les champs que le désassembleur a promu à l’aide des propriétés promues suivantes (définies dans le A4SWIFT Schéma de propriété, Microsoft.Solutions.A4SWIFT.Property.PropertySchema) :  
  
-   **A4SWIFT_MessageType**  
  
-   **A4SWIFT_MessageType2** (facultatif si **A4SWIFT_MessageTypes** est utilisé)  
  
-   **A4SWIFT_SecondaryMessageType** (facultatif)  
  
 Pour plus d’informations sur ces autres propriétés promues et, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
> [!NOTE]
>  Si vous définissez le schéma d’en-tête SWIFT à **aucun**, vous devez spécifier un schéma de l’échange complet pour le **SWIFT échange schéma** propriété. Dans ce cas, le désassembleur utilise le schéma d’échange spécifié pour analyser tous les messages qui reçoit d’A4SWIFT. Autrement dit, vous désactivez la résolution de schéma dynamique et configurez le pipeline pour recevoir uniquement les messages dont le type correspond au schéma de l’échange spécifié.  
  
 A4SWIFT installe un schéma d’en-tête SWIFT par défaut (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) qui peut analyser les données d’en-tête standard SWIFT et qui possède les propriétés promues nécessaires pour faciliter la résolution de schéma dynamique.  
  
 Le schéma d’en-tête SWIFT par défaut a les champs promus suivants :  
  
-   **SWIFTHeader/ApplicationHeaderBlock_Input/MessageType**. Le désassembleur promeut à l’aide de la **A4SWIFT_MessageType** propriété.  
  
-   **SWIFTHeader/ApplicationHeaderBlock_Output/MessageType**. Le désassembleur promeut à l’aide de la **A4SWIFT_MessageType2** propriété.  
  
-   **SWIFTHeader/UserHeaderBlock/ValidationFlag_119**. Le désassembleur promeut à l’aide de la **A4SWIFT_MessageType** propriété.  
  
 Le désassembleur utilise **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** par défaut en tant que le schéma d’en-tête si vous définissez les propriétés de configuration de schéma d’en-tête SWIFT et schéma de l’échange SWIFT » « None ».  
  
## <a name="swift-assembler"></a>Assembleur SWIFT  
 Comme le désassembleur SWIFT, l’assembleur SWIFT a la possibilité de détecter le type de message d’un message sortant dynamiquement et de charger le schéma approprié nécessaire pour sérialiser le message. Cette fonctionnalité vous permet de configurer un seul pipeline à l’aide de l’assembleur SWIFT pour traiter les messages SWIFT de n’importe quel type de messages SWIFT. Contrairement à l’assembleur de fichier plat BizTalk native, l’assembleur SWIFT ne nécessite pas vous permet de créer un pipeline d’envoi distinct pour chaque type de message que A4SWIFT pouvez rencontrer.  
  
 Résolution de schéma dynamique dans l’assembleur SWIFT est beaucoup plus simple que dans le désassembleur rapide, car l’assembleur effectue le travail de la sérialisation XML au format de fichier plat SWIFT. Le code XML qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] donne à l’assembleur SWIFT pour sérialisation contient les message type informations et de schéma, qui permet de l’assembleur SWIFT directement à charger le schéma approprié pour la sérialisation. Par conséquent, l’assembleur SWIFT n’a pas de toutes les possibilités de configuration pour les schémas d’en-tête et d’échange : il utilise toujours le schéma spécifié dans le code XML qu’il sérialise.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)