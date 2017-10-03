---
title: "La sécurité avec l’adaptateur Oracle E-Business Suite et BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d4a816c-505d-4d5d-9eb9-04847f9b5861
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe73785ee49b260754a35e27f8ffa2ef2bcaa6bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-oracle-e-business-suite-adapter-and-biztalk-server"></a>Sécurité avec l’adaptateur Oracle E-Business Suite et BizTalk Server
Lorsque vous configurez un port d’envoi ou un port de réception (emplacement) à l’aide de l’Administration de BizTalk Server de la console ou utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir les informations d’identification pour Oracle E-Business Suite. Il est important de fournir ces informations d’identification de manière sécurisée pour aider à les empêcher d’accessibles à d’acteurs potentiellement malveillants. Cette rubrique explique comment fournir plus de manière sécurisée les informations d’identification pour le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] pour les solutions BizTalk Server.  
  
 Une description plus générale de la sécurité dans le cadre de solutions BizTalk est un sujet vaste et dépasse le cadre de cette documentation. Pour savoir comment vous pouvez sécuriser vos solutions BizTalk, consultez [sécurisé et protéger vos messages BizTalk](../../core/secure-and-protect-your-biztalk-messages.md).   
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in-or-add-adapter-metadata-wizard"></a>Comment protéger informations d’identification lorsque vous utilisez le Consume Adapter Service BizTalk Project Add-in ou l’Assistant Ajout d’adaptateur métadonnées ?  
 Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous pouvez fournir des informations d’identification pour se connecter à Oracle E-Business Suite dans les deux emplacements suivants :  
  
-   Sur le **sécurité** onglet dans le **configurer l’adaptateur** boîte de dialogue. Cela garantit que vos informations d’identification ne seront pas affichées dans le **configurer un URI** champ le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] boîte de dialogue, où toute personne ayant accès à l’écran de votre ordinateur peut les lire.  
  
-   Dans le **OracleUserName** et **OraclePassword** propriétés de liaison de la **propriétés de liaison** onglet dans le **configurer l’adaptateur** boîte de dialogue. Pour des raisons de sécurité, le **OraclePassword** propriété de liaison n’est pas disponible dans le fichier XML (fichier) de liaison généré suite à l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
    > [!NOTE]
    >  À l’aide de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ne génère pas de n’importe quel fichier de liaison.  
  
 Pour plus d’informations sur la façon de récupérer des schémas de message à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], consultez [obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>Comment protéger les informations d’identification lorsque vous configurez un Port d’envoi ou un emplacement de réception ?  
 Les solutions BizTalk utilisent l’adaptateur Microsoft BizTalk WCF-Custom ou WCF-Oracle eBusiness Suite à utiliser les services WCF. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est une liaison WCF qui permet aux clients d’utiliser Oracle E-Business Suite comme s’il s’agissait d’un service WCF. Consomment des solutions BizTalk le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] via les ports d’envoi et emplacements de réception qui sont configurés pour utiliser l’adaptateur WCF-Custom ou WCF-OracleEBS, qui est, à son tour, configuré pour utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] comme type de transport. Pour plus d’informations sur la configuration des ports d’envoi et réception de ports (emplacements de réception), y compris comment configurer l’adaptateur WCF-Custom, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
 Vous configurez les informations d’identification Oracle E-Business Suite à partir de la **informations d’identification** onglet de la **propriétés du Transport WCF-Custom** boîte de dialogue pour les ports d’envoi ou de la **autres** onglet de la **propriétés du Transport WCF-Custom** boîte de dialogue pour les emplacements de réception. Étant donné que l’adaptateur WCF-Custom ou WCF-Oracle eBusiness Suite prend en charge Enterprise Single Sign-On (SSO), vous pouvez choisir de fournir un nom d’utilisateur et un mot de passe ou une authentification unique associée à l’application sur un de ces onglets. Les rubriques suivantes abordent les deux options.  
  
### <a name="user-name-password-credentials"></a>Informations d’identification de mot de passe utilisateur  
 Vous ne devez fournir un nom d’utilisateur et un mot de passe à partir de la **informations d’identification** onglet (pour les ports d’envoi) ou le **autres** onglet (pour les emplacements de réception) dans le **propriétés du Transport WCF-Custom**boîte de dialogue. Cela offre les avantages suivants :  
  
-   Vos informations d’identification ne s’affichera pas dans le **adresse (URI)** champ de la boîte de dialogue. Ainsi, ceux qui ont accès à l’écran (ou qui disposent des autorisations leur permettant d’afficher le port d’envoi ou de propriétés de l’emplacement de réception) de voir vos informations d’identification.  
  
-   Votre mot de passe n’est pas être écrite dans le fichier de liaison si vous exportez le port d’envoi ou de liaison de port de réception. Cela empêche quiconque ayant accès au fichier à partir de l’affichage de votre mot de passe.  
  
### <a name="oraclepassword-binding-property"></a>Propriété de liaison OraclePassword  
 La valeur que vous spécifiez dans le **OraclePassword** liaison de propriété pour l’envoi ou réception port n’est disponible en texte clair lorsque vous exportez des liaisons à partir d’une application dans BizTalk Server. Par conséquent, après avoir exporté un fichier de liaison à partir d’une application dans BizTalk Server, vous devez supprimer manuellement la valeur de la **OraclePassword** propriété de liaison à partir du fichier de liaison et de spécifier à nouveau sur chaque ordinateur hôte où le liaison exporté sera utilisé.  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>Enterprise Single Sign-On et l’authentification unique des Applications associées  
 Vous pouvez configurer l’adaptateur WCF-Custom pour utiliser Enterprise Single Sign-on (SSO) pour obtenir les informations d’identification d’Oracle E-Business Suite. L’authentification unique utilise une base de données et un secret pour chiffrer et stocker les informations d’identification de l’utilisateur. Il fournit également des services pour mapper les comptes Microsoft Windows aux informations d’identification secondaires qui sont utilisées pour accéder à un système principal. À l’aide de l’authentification unique, vous pouvez mapper un compte Windows à un nom d’utilisateur et le mot de passe sur la base de données Oracle.  
  
 L’authentification unique utilise *applications associées* et *mappages SSO* pour mapper les informations d’identification pour le système principal. Une application associée est une entité logique dans l’authentification unique qui fait référence à un système ou une application qui nécessite des informations d’identification secondaires. Un mappage de l’authentification unique est associé à une application associée. Il est mappé à un compte Windows pour les informations d’identification secondaires utilisées par ce compte pour accéder à l’application ou le système associé. Un mappage de l’authentification unique peut être associé à un compte d’utilisateur Windows ou à un groupe.  
  
 Pour utiliser l’authentification unique avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez procédez comme suit.  
  
1.  Créer une application associée dans l’authentification unique pour contenir des informations d’identification de mot de passe de l’utilisateur d’Oracle E-Business Suite. Cette étape est souvent effectuée par une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
2.  Créez un utilisateur ou un mappage de groupe pour l’application associée qui mappe votre compte Windows pour le nom d’utilisateur et un mot de passe qui sont utilisées pour établir une connexion avec la base de données Oracle. Selon votre installation, un utilisateur peut être en mesure d’effectuer cette étape, ou il peut nécessiter une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
> [!NOTE]
>  Lorsque configuré pour l’authentification unique, l’adaptateur WCF-Custom utilise les services fournis par l’authentification unique pour obtenir le nom d’utilisateur Oracle et le mot de passe à partir de la base de données SSO. Il fournit ces (non chiffré) à la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], de sorte que l’adaptateur peut ouvrir une connexion à Oracle E-Business Suite. SSO ne fournit aucun chiffrement ou la protection via la connexion entre le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et Oracle E-Business Suite.  
  
 Pour plus d’informations sur l’utilisation de l’authentification unique, notamment des informations sur la création d’applications associées et les mappages de l’authentification unique, consultez [à l’aide de l’authentification unique](../../core/using-sso.md). Pour plus d’informations sur l’authentification unique, consultez [implémentation Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md). 
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>La propriété de liaison AcceptCredentialsInUri  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces le **AcceptCredentialsInUri** propriété de liaison. Cette propriété détermine si la base de données Oracle ou les informations d’identification Oracle E-Business Suite sont autorisées dans l’URI de connexion. Par défaut, **AcceptCredentialsInUri** est **false** et [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception si les informations d’identification sont incluses dans l’URI.  
  
 Cette propriété est visible, car il existe certains scénarios de programmation qui requièrent les informations d’identification présentes dans l’URI de connexion. Il ne doit jamais être le cas lorsque vous configurez un port d’envoi ou un emplacement de réception ou lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il est recommandé de ne pas définir **AcceptCredentialsInUri** à **true**. Pour plus d’informations sur la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 Le **AcceptCredentialsInUri** propriété de liaison n’est pas disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] dans les **liaison** onglet lors de la configuration WCF-Custom ou WCF-OracleEBS de réception ou port d’envoi. Pour définir la valeur de la **AcceptCredentialsInUri** propriété de liaison, vous devez ouvrir le fichier de liaisons de l’adaptateur (fichier XML) qui est créé une fois que vous avez généré à l’aide des métadonnées du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], puis recherchez la propriété liaison dans le fichier. Spécifiez une valeur appropriée pour cette propriété de liaison, enregistrez le fichier de liaison, puis importer le fichier de liaison dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Consultez [l’importation des liaisons](http://msdn.microsoft.com/library/7af35a2e-fb7c-48a1-af28-93427403a745) pour obtenir des instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)  
 [Meilleures pratiques pour sécuriser l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)
