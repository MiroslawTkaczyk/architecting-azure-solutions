Opis sytuacji: Jesteś architektem w firmie o europejskim zasięgu i rozpoczynasz w swojej firmie budowanie rozwiązań opartych o Microsoft Azure. Jako architekt ustaliłeś kilka pryncypiów projektowych, które powinny być respektowane przy każdym wdrożeniu:
1.	Każdy projekt powinien używać konwencji nazw dla grup i zasobów zgodnych z konwencją firmy
2.	Infrastruktura, budowana w Azure pod środowiska czy aplikacje powinna być zawsze budowana z wykorzystaniem Azure Resource Managera i template’ów. Jeśli jest to duże wdrożenie, powinny być użyte tzw. Linked Templates.
3.	Jeśli to konieczne, należy zbudować własny model ról za pomocą RBAC
4.	Docelowo, wszystkie kluczowe ustawienia, tak jak np. nazwy lokalnych administratorów i hasła powinny być pobierane z Azure KeyVault

 #TYDZIEN3.1 „Zbuduj prostą konwencję nazewniczą dla min. takich zasobów jak Grupa Zasobów, VNET, Maszyn Wirtualna, Dysk, Konta składowania danych. Pamiętaj o ograniczeniach w nazywaniu zasobów, które występują w Azure”
Konwencja nazewnicza.

Rozwiązanie:
Nazwy wszystkich zasobów zaczynają się od prefixu składającego się z: symbolu oddziału "branch", symbolu projektu "project", rodzaju środowiska "env" deklarowanych w parametrach szablonu. Dodatkowo dodawany jest symbol zasobu i wyróżniający go numer. Np:

Disk:

 "brunch""project""env""osDisc""number"
 PolSchTestOsDisc1
Virtual Machine:

 "brunch""project""env""Vm""number"
PolSchTestVm2
  
  
#TYDZIEN3.2 „ Zbuduj prosty ARM Template (możesz wykorzystać już gotowe wzorce z GitHub), który wykorzystuje koncepcję Linked Templates. Template powinien zbudować środowisko złożone z jednej sieci VNET, podzielonej na dwa subnety. W każdy subnecie powinna powstać najprostsza maszyna wirtualna z systemem Ubuntu 18.04 a na każdym subnecie powinny zostać skonfigurowane NSG.”

Wdrożenie:

az group create --name szkola --location westeurope

az group deployment create -g szkola --template-uri https://raw.githubusercontent.com/MiroslawTkaczyk/architecting-azure-solutions/master/homework/3.2/azuredeploy.json 


#TYDZIEN3.3 „Zbuduj najprostrzą właśną rolę RBAC, która pozwala użytkownikowi uruchomić maszynę, zatrzymać ją i zgłosić zgłoszenie do supportu przez Portal Azure”

https://github.com/MiroslawTkaczyk/architecting-azure-solutions/tree/master/homework/3.3

#TYDZIEN3.4 „Spróbuj na koniec zmodyfikować template tak, by nazwa użytkownika i hasło do każdej maszyny z pkt. 2 było pobierane z KeyVault.„

https://github.com/MiroslawTkaczyk/architecting-azure-solutions/tree/master/homework/3.4
