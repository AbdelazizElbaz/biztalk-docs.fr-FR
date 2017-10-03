---
title: "La sécurité avec l’adaptateur SAP et BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials, protecting
- Enterprise Single Sign-On
- security, when using BizTalk Server
- security, protecting credentials
- SSO
ms.assetid: 702cd0f9-d8e1-4dad-8774-b552481d5390
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4689424deced097d901464263d75e5ae10e4b99f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-sap-adapter-and-biztalk-server"></a>Sécurité avec l’adaptateur SAP et de BizTalk Server
Lorsque vous configurez un port d’envoi ou un port de réception (emplacement) à l’aide de l’Administration de BizTalk Server de la console ou utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir les informations d’identification pour le système SAP. Il est important de fournir ces informations d’identification de manière sécurisée pour aider à les empêcher d’accessibles à d’acteurs potentiellement malveillants. Cette rubrique explique comment fournir plus de manière sécurisée les informations d’identification pour le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] pour les solutions BizTalk Server.  
  
 Une description plus générale de la sécurité dans le cadre de solutions BizTalk est un sujet vaste et dépasse le cadre de cette documentation. Pour savoir comment vous pouvez rendre vos solutions BizTalk plus sécurisée, consultez le [sécurisé et protéger vos messages BizTalk](../../core/secure-and-protect-your-biztalk-messages.md).  
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in"></a>Comment protéger informations d’identification lorsque vous utilisez le Consume Adapter Service BizTalk Project Add-in ?  
 Lorsque vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir un nom d’utilisateur et un mot de passe pour le système SAP. Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. Cela garantit que vos informations d’identification ne seront pas affichées dans le **Uri** champ le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] boîte de dialogue, où toute personne ayant accès à l’écran de votre ordinateur peut les lire. Pour plus d’informations sur la façon de récupérer des schémas de message à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour le système SAP, consultez [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>Comment protéger les informations d’identification lorsque vous configurez un Port d’envoi ou un emplacement de réception ?  
 Les solutions BizTalk utilisent l’adaptateur Microsoft BizTalk WCF-Custom pour utiliser les services WCF. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison WCF personnalisée qui permet aux clients d’utiliser le système SAP, comme s’il s’agissait d’un service WCF. Consomment des solutions BizTalk le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via les ports d’envoi et emplacements de réception qui sont configurés pour utiliser l’adaptateur WCF-Custom, qui est, à son tour, configuré pour utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme type de transport. Pour plus d’informations sur la configuration des ports d’envoi et réception de ports (emplacements de réception), y compris comment configurer l’adaptateur WCF-Custom, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  
  
 Vous configurez les informations d’identification du système SAP à partir de la **informations d’identification** onglet de la **propriétés du Transport WCF-Custom** boîte de dialogue pour les ports d’envoi ou de la **autres** onglet du  **Propriétés du Transport WCF-Custom** boîte de dialogue pour les emplacements de réception. Étant donné que l’adaptateur WCF-Custom prend en charge Enterprise Single Sign-On (SSO), vous pouvez choisir de fournir un nom d’utilisateur et mot de passe ou une application associée SSO sur un de ces onglets. Les rubriques suivantes abordent les deux options.  
  
### <a name="user-name-password-credentials"></a>Informations d’identification de mot de passe utilisateur  
 Vous ne devez fournir un nom d’utilisateur et un mot de passe à partir de la **informations d’identification** onglet (pour les ports d’envoi) ou le **autres** onglet (pour les emplacements de réception) dans le **propriétés du Transport WCF-Custom**boîte de dialogue. Cela offre les avantages suivants :  
  
-   Vos informations d’identification ne s’affichera pas dans le **Uri** champ de la boîte de dialogue. Ainsi, ceux qui ont accès à l’écran (ou qui disposent des autorisations leur permettant d’afficher le port d’envoi ou de propriétés de l’emplacement de réception) de voir vos informations d’identification.  
  
-   Votre mot de passe n’est pas être écrite dans le fichier de liaison si vous exportez le port d’envoi ou de liaison de port de réception. Cela empêche quiconque ayant accès au fichier à partir de l’affichage de votre mot de passe.  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>Enterprise Single Sign-On et l’authentification unique des Applications associées  
 Vous pouvez configurer l’adaptateur WCF-Custom pour utiliser l’authentification unique pour obtenir les informations d’identification pour le système SAP. L’authentification unique utilise une base de données et un secret pour chiffrer et stocker les informations d’identification de l’utilisateur. Il fournit également des services pour mapper les comptes Microsoft Windows aux informations d’identification secondaires qui sont utilisées pour accéder à un système principal. À l’aide de l’authentification unique, vous pouvez mapper un compte Windows à un nom d’utilisateur et un mot de passe sur le système SAP.  
  
 L’authentification unique utilise *applications associées* et *mappages SSO* pour mapper les informations d’identification pour le système principal. Une application associée est une entité logique dans l’authentification unique qui fait référence à un système ou une application qui nécessite des informations d’identification secondaires. Un mappage de l’authentification unique est associé à une application associée. Il est mappé à un compte Windows pour les informations d’identification secondaires utilisées par ce compte pour accéder à l’application ou le système associé. Un mappage de l’authentification unique peut être associé à un compte d’utilisateur Windows ou à un groupe.  
  
 Pour utiliser l’authentification unique avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez procédez comme suit.  
  
1.  Créer une application associée dans l’authentification unique pour stocker des informations d’identification de mot de passe pour le système SAP de l’utilisateur. Cette étape est souvent effectuée par une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
2.  Créez un utilisateur ou un mappage de groupe pour l’application associée qui mappe votre compte Windows pour le nom d’utilisateur et un mot de passe qui sont utilisées pour établir une connexion avec le système SAP. Selon votre installation, un utilisateur peut être en mesure d’effectuer cette étape, ou il peut nécessiter une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
> [!NOTE]
>  Lorsque configuré pour l’authentification unique, l’adaptateur WCF-Custom utilise les services fournis par l’authentification unique pour obtenir le nom d’utilisateur SAP et le mot de passe à partir de la base de données SSO. Il fournit ces (non chiffré) à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], de sorte que l’adaptateur peut ouvrir une connexion au système SAP. SSO ne fournit aucun chiffrement ou la protection via la connexion entre le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et le système SAP.  
  
 Pour plus d’informations sur l’utilisation de l’authentification unique, notamment des informations sur la création d’applications associées et les mappages de l’authentification unique, consultez [à l’aide de l’authentification unique](../../core/using-sso.md). Pour plus d’informations sur l’authentification unique, consultez [implémentation Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).  
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>La propriété de liaison AcceptCredentialsInUri  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces le **AcceptCredentialsInUri** propriété de liaison. Cette propriété détermine si les informations d’identification du système SAP sont autorisées dans l’URI de connexion. Par défaut, **AcceptCredentialsInUri** est **false** et [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] lève une exception si les informations d’identification sont incluses dans l’URI.  
  
 Cette propriété est visible, car il existe certains scénarios de programmation qui requièrent les informations d’identification présentes dans l’URI de connexion. Il ne doit jamais être le cas lorsque vous configurez un port d’envoi ou un emplacement de réception ou lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Dans ce cas, il est recommandé de ne pas définir **AcceptCredentialsInUri** à **true**. Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’ORacle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 Le **AcceptCredentialsInUri** propriété de liaison n’est pas disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] dans le **liaison** onglet lors de la configuration de WCF-Custom SAP WCF de réception ou port d’envoi. Pour définir la valeur de la **AcceptCredentialsInUri** propriété de liaison, vous devez ouvrir le fichier de liaisons de l’adaptateur (fichier XML) qui est créé une fois que vous avez généré à l’aide des métadonnées du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], puis recherchez la propriété liaison dans le fichier. Spécifiez une valeur appropriée pour cette propriété de liaison, enregistrez le fichier de liaison, puis importer le fichier de liaison dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md) pour obtenir des instructions.  
  
## <a name="see-also"></a>Voir aussi  
[Meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
 [Sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   