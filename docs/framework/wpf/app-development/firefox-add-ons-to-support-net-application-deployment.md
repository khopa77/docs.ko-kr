---
title: .NET 애플리케이션 배포를 지원하기 위한 Firefox 추가 기능
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 56f5f633092d8aa0bfabdb0570ec26f14221838d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124613"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET 애플리케이션 배포를 지원하기 위한 Firefox 추가 기능
Firefox 용 WPF (Windows Presentation Foundation) 플러그 인 및 Firefox 용 .NET Framework 길잡이는 Xbap (XAML 브라우저 응용 프로그램), 느슨한 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]및 ClickOnce 응용 프로그램을 Mozilla Firefox 브라우저에서 사용할 수 있도록 합니다.  
  
## <a name="wpf-plug-in-for-firefox"></a>Firefox 용 WPF 플러그 인  
 Firefox 용 WPF 플러그 인을 사용 하면 Xbap 및 느슨한 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 파일을 탐색 하 고 Firefox 브라우저의 최상위 또는 HTML IFRAME에서 실행할 수 있습니다. XBAP는 웹 서버에 게시 하 여 지원 되는 브라우저 내에서 시작할 수 있는 WPF 응용 프로그램입니다. 느슨한 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]는 XML 파일과 매우 유사 하 게 지원 되는 브라우저에서 탐색 하 고 표시할 수 있는 XAML 전용 파일입니다.  
  
 Firefox 용 WPF 플러그 인은 .NET Framework 3.5와 함께 설치 됩니다. Windows 7에는 .NET Framework 3.5이 포함 되어 있지만 Firefox 용 WPF 플러그 인은 포함 되지 않습니다. Windows 7에는 Firefox 용 WPF 플러그 인을 설치할 수 없습니다.  
  
 .NET Framework 4에는 Firefox 용 WPF 플러그 인이 포함 되어 있지 않습니다. 그러나 .NET Framework 3.5 및 .NET Framework 4가 모두 설치 되어 있는 경우 Firefox 용 WPF 플러그 인이 .NET Framework 3.5와 함께 설치 됩니다. 따라서 WPF 호스트에서 프레임 워크의 올바른 버전을 로드 하기 때문에 .NET Framework 4 응용 프로그램은 계속 실행 됩니다. 자세한 내용은 [WPF 호스트 (presentationhost.exe)](wpf-host-presentationhost-exe.md)를 참조 하세요.  
  
## <a name="net-framework-assistant-for-firefox"></a>Firefox용 .NET Framework Assistant  
 Firefox 용 .NET Framework 길잡이를 사용 하면 독립 실행형 ClickOnce 응용 프로그램을 Firefox 브라우저에서 실행할 수 있습니다. Firefox에 대 한 .NET Framework 길잡이는 Firefox 브라우저 전후에 설치 될 때 동일 하 게 작동 합니다. Firefox 브라우저가 시작 되 고 .NET Framework 3.5 s p 1이 설치 되 면 Firefox는 Firefox 용 .NET Framework 길잡이를 찾아서 설치 합니다. 사용자는 Firefox에 대 한 .NET Framework 길잡이를 구성 하 여 다음을 수행할 수 있습니다.  
  
- ClickOnce 응용 프로그램을 실행 하기 전에 확인 합니다.  
  
- 설치 된 .NET Framework 버전을 모두 보고 하거나 최신 버전만 보고 합니다.  
  
 Firefox 용 .NET Framework 길잡이는 .NET Framework 3.5 s p 1에 포함 되어 있습니다. Firefox 용 .NET Framework 길잡이를 제거 하는 방법에 대 한 자세한 내용은 [firefox 용 .NET Framework 길잡이를 제거](https://support.microsoft.com/help/963707/how-to-remove-the-net-framework-assistant-for-firefox)하는 방법을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- [WPF 애플리케이션 배포](deploying-a-wpf-application-wpf.md)
- [WPF XAML 브라우저 애플리케이션 개요](wpf-xaml-browser-applications-overview.md)
- [Firefox용 WPF 플러그 인 설치 여부 확인](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
