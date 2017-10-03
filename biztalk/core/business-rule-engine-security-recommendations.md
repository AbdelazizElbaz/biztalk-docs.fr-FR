---
title: "Recommandations de sécurité de moteur de règle métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, business rules
- Business Rules Framework, security
- business rules, security
ms.assetid: d5df1cd0-112a-4c72-b95d-cbcd1bc6a2c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d7402a1cc36ef3d9473c3303da79b0c23f46bf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rule-engine-security-recommendations"></a>Recommandations de sécurité de moteur de règle métier
Le moteur des règles d'entreprise est le composant d'exécution de l'infrastructure des règles d'entreprise. Grâce à cette infrastructure, vous pouvez connecter des règles déclaratives très lisibles et riches sur le plan sémantique à n'importe quel objet métier (composant .NET), document XML ou table de base de données. Pour plus d’informations sur l’infrastructure de règle d’entreprise, consultez [création et à l’aide des règles d’entreprise](../core/creating-and-using-business-rules.md). Pour plus d’informations sur le moteur de règles d’entreprise, consultez [du moteur de règles](../core/rule-engine.md).  
  
 Aucun groupe d'utilisateurs Windows n'est associé au moteur des règles d'entreprise, uniquement des comptes individuels. BizTalk Server limite l'accès aux ressources du moteur des règles d'entreprise par l'intermédiaire de deux rôles SQL Server :  
  
 Le rôle RE_Admin_Users SQL Server est destiné aux utilisateurs qui doivent effectuer des tâches administratives dans le moteur des règles d'entreprise, telles que déployer des règles. Les membres de ce rôle sont les administrateurs BizTalk.  
  
 Le rôle RE_Host_Users est associé à tous les autres utilisateurs du moteur des règles d'entreprise, qui n'ont pas besoin de droits administratifs et dont les tâches consistent à lire et exécuter les règles. Les membres de ce groupe incluent ceux du rôle BizTalk_Host_Users. Les rôles SQL Server permettent également d'implémenter des autorisations liées au moteur des règles d'entreprise indépendantes des autorisations BizTalk Server. Pour plus d’informations sur les autorisations minimales requises pour utiliser le moteur de règles d’entreprise, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md). Il est recommandé de respecter les informations ci-dessous pour la sécurisation et le déploiement du moteur des règles d'entreprise dans votre environnement.  
  
-   BizTalk Server utilise le compte qui a servi à installer la connexion du service de mise à jour pour les droits associés au service, et l'ajoute au rôle RE_Host_Users SQL Server de la base de données du moteur des règles d'entreprise. Si le compte utilisé pour l'installation n'est pas celui que vous allez utiliser pour exécuter le service de mise à jour, vous devez supprimer le compte d'installation du rôle RE_Host_Users SQL Server.  
  
-   Si vous utilisez le composant Service de mise à jour, vous devez l'installer sur tous les ordinateurs d'exécution BizTalk. Pour extraire une règle de la base de données du moteur de règles, le service de mise à jour se fait passer pour l'appelant du service.  
  
-   Par défaut, tous les hôtes BizTalk ont le même niveau d'accès aux artefacts du moteur de règles. Il n'existe pas de limitation de sécurité liée aux hôtes. Vous pouvez configurer une sécurité liée aux stratégies par le biais des API du moteur de règles. Pour plus d’informations sur la façon de configurer la sécurité liée aux stratégies, consultez [sécurité infrastructure des règles d’entreprise](../core/business-rules-framework-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports pour les serveurs de traitement](../core/ports-for-the-processing-servers.md)