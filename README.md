# TheoryGraph
Реаизованы матричные оперции на основе метода Гаусса - вычисление обратной матрицы, определителя, ранга матрицы и возведения матрицы в степень.

Реализованы следующие алгоритмы: DFS, BFS, алгоритм Прима, Краскала, Дейкстры, Белмана-Форда, Джонсона, Таргяна, алгоритм проверки на двудольность и класс графа.

Также предстваленна краткая выжимка из теории графов: основные матрицы, связность, эйлеров и гамильтонов цикл, деревья, разрезы, планарные графы, многогранники, потоки и центральность.

Основные определения.

  Есть два основых определения графа комбинаторное и топологическое графа. Мы будем пока пользоваться комбинаторным определением графа.
  
  Опр. Графом G называется тройка G = (V,E,f), V-мн-во вершин, E- мн-во ребер, f : E -> V1 U V2, где Vk - мн-во k элементных подмножеств V, f - отображение инцидентности.
  
  Опр. если вершина v принадлежит f(e), то говорят, что вершина инцидентна ребру (и наоборот тоже верно).
  
  Граф на n вершинах и m ребрах, будем обозначать как G(n,m), V(G) - кол-во вершин G, E(G) - кол-во ребер G.
  
  Опр. Кратные ребра - ребра инцидентные одним и тем же вершинам. Петля - ребро инцидентное  ровно одной вершине.
  
  Опр. Простой граф - граф без петель и кратных ребер.
  
  Опр. Степень вершины - кол-во ребр инцидентных вершине.
  
  Далее для простоты считаем, что E = V1 U V2, все вершины занумерованы от 1 до n и, что все графы простые.
  
  Опр. Подграф - подмножество ребер.
  
  Опр. Цикл в графе - замкнутый маршрут.
  
  Опр. Графы H и G изоморфны, если существует перенумерация вершин графа H, чтобы получился граф G.
  
  Проверка на изиморфизм это NP трудная задача( задача которая решается за полиномиальное время от входных данных ).
  
  Лемма о рукопожатиях
    Сумма степеней всех вершин равна удвоенному числу ребер.


Основные матрицы.
  
  Опр. Матрица смежности А = (a(i,j)) a(i,j) = число ребер из i в j.
  
  Лемма
    (A)^k(i,j) = число путей из i в j (А матрица смежности).
    
  Опр. Матрица Лапласса L = (d1,..,dn по диагонали) - A .
  
  Опр. B = матрица инцидентности, b(i,j) = 1, если из i вершины выходит j ребро, -1 если входит, 0 иначе.
  
  Лемма.
    L = B*B^T


  
Cвязность.

  Опр. Слабая св-ть - неориентированный граф, соответствующий ориентированому связен.
  
  Опр. Полусв-ть - для любых вершин u,v, существует путь либо из u в v, либо наоборот.
  
  Опр. Сильная св-ть - для любых вершин u,v, существует путь из u в v и наоброт.
  
  Опр. Компонентна св-ти - максимальный подграф, который связный в смысле выбранного определения связности.
  
  Т.
    Неориентированный G(n,m), где  m > C из n-1 по 2, связен
    
  Лемма.
    G(n,m) неориентированный, то rank B = n- кол-во компонент связности






Гамильтоновый  и эйлеров цикл.

  Гамильонов цикл - проходим все вершины по одному разу.
  
  Эйлеров цикл - проходим все ребра по одному разу.
  
  Т. Критерий эйлеровости графа.
    Связный граф эйлеров, если и только если  степени всех его вершин чётны.
    
  Т. ОРЕ
      u and v не смежны и deg u + deg v >= n, то G гамильтонов.
      
  Т. Дирака
      deg u >= n/2, то G гамильтонов.





Деревья.

  Опр. Дерево - граф без циклов.
  
  Опр. Лист ( висячая вершина ) - вершина степени 1.
  
  Лемма о 2-x листах.
    В дереве два листа.
    
  Опр. Если V(G) = n, G' подграф в G, V(G') = n и G'- дерево, то G' остовное дерево.
  
  BFS (поиск в ширину).
  
  BFS следует концепции «расширяйся, поднимаясь на высоту птичьего полета» («go wide, bird’s eye-view»).
  Вместо того, чтобы двигаться по определенному пути до конца, BFS предполагает движение вперед по одному соседу за раз.
  
  DFS (поиск в глубину).
  
  Принцип его работы совпадает с его названием, данный алгоритм идет "внутрь" графа, до того момента как ему становится некуда идти,
  затем возвращается в предыдущую вершину и снова идет от нее до тех пор, пока есть куда идти. И так далее. 
  
  Оба алгоритма работают за O(V+E).
  
  Т. Критерий дерева.
    G(n,m) дерево равносильно m = n-1.
    
  Минимальное остовное дерево ищет алгоритм Прима и алгоритм Краскала.
  
  Алгоритм Прима.
    Пусть построен подграф, посмотрим на все ребра выходящие из вершин, но не содержащиеся в подграфе и выберем самое легкое ребро.
  
  Алгоритм Краскала.
    Сортируем все ребра по весу, в порядке возрастания.
    Берем самое легкое ребро, проверяем граф на ацикличность (отсутствие циклов) и так далее (если получился цикл, то не берем это ребро), пока ребер не n-1.
    
  Оба Алгоритма работают за O(V+E), а если сортируем то ещё логарифм возникает.
  
  Факт "Как строить карту".
    Берем сетку, делаем остовное дерево и раздуваем в нём ребра, получаем карту.
  
  Т. Киргофа.
    G неориентированный связный, то любое алгебраическое дополнение L - это кол-во остовных деревьев.
  
  Опр. Полный граф - неориентированный граф, в котором каждая пара различных вершин смежна. (Клика)
  
  Опр. Полный двудольный граф -  специальный вид двудольного графа, у которого любая вершина первой доли соединена со всеми вершинами второй доли вершин. (Биклика)
  
  Т. Кэлли.
      Кол-во остовных деревьев полного графа G(n,m) это n^(n-2).
      Кол-во остовных деревьев полного двудольного графа Kn,m = n^n-1 * m^m-1.
      
  Лемма.
    G двудольный, если и только если не содержит нечётных циклов.
  
  




Алгоритмы поиска кратчайшего пути.
    1) Если веса >0 то алгоритм Дейкстры
    2) Алгоритм Белмана-Форда
    3) Cоставление матрицы путей алгоритм Джонсона
  
  



  
Разрезы.

  Опр. n - вершинный разрез (m - реберный разрез) - это такие n вершин (m ребер), что после их удаление, граф становится не связным.
  
  Опр. Граф называется k - вершинно (реберно) связный, если не существует k-1 разрезов вершин (ребер)
  
  1) 1- вершинно связный - просто связный
  2) Kn по определению - n-1 вершинно связный
     
  Опр. Вершинно независымые пути не пересекаются по вершинам (аналогично реберно независимые пути)
  
  Т. Менгера
    k-вершинно (реберно) связный, если и только если для любых вершин существует k-вершинно или реберно независимых путей.
  
  Т. (k,l,d) - граф
    Для любых к<=l<=d (где k,l,d - натуральные), cуществует граф, где граф k - вершинно связный, l - реберно связный, d - минимальная степень вершин
    
  Опр. Мост - ребро, соотвествующие 1 - реберному разрезу.
  
  Алгоритм Таргяна ищет в графе все мосты





Плоские (планарные) графы.

  Здесь пользуемся топологическим определением графа
  
  Опр. Представление графа на плоскости, в котором вершины графа представлены различными точками, а рёбра кривыми Жордана (связанные куски кривых Жордана), соединяющими соответствующие пары точек.
    Точки, представляющие вершины графа, и дуги, представляющие рёбра, называются вершинами и рёбрами топологического графа. 
    
  Опр. Планарный граф - граф у которого существует вложение (репрезентация) на плоскость.
  
  Т. Жордана.
    Область ограниченная кривой D разбивает плоскость на Int(D) и Out(D)
  
  Т. Эйлера.
    V - E + F = 2, где F число граней (области ограниченные простыми циклами - F(i)) и добавляют внешнию грань - пересечение всех Out(F(i)).
  
  Следствие.
    V - E + F = 1 + c, где с - кол-во компонент связности.
  
  Неравенства с плоскими графами
    Е <= 3V - 6,  2E >= 3F.
  
  Лемма
    У любого плоского графа есть вершинна степени <=5.
  
  Т. Понтрягина - Куратовского
    G - планарный, если и только если он не содержит подграфов изоморфных K5 и K3,3.





Многогранники

  Опр. Пусть 𝐿 – замкнутая не самопересекающаяся ломаная. По теореме Жордана, она разбивает плоскость на две компоненты (ограниченную и неограниченную).
  Многоугольником называется замкнутая не самопересекающаяся ломаная вместе с ограниченной компонентой.
  
  Опр. Два плоских многоугольника, расположенных в пространстве, назовем смежными по ребру 𝑎, если отрезок 𝑎 является их общей стороной
  
  Опр. Многогранной поверхностью называется набор многоугольников, расположенных в пространстве так, что для каждой стороны каждого многоугольника
  задан ровно один (другой) многоугольник из этого набора, смежный с ним по ребру 𝑎, причем это отношение симметрично.

  Опр. Многогранная поверхность называется вложенной, если:
  1) любая внутренняя точка грани принадлежит только этой грани,
  2) любая внутренняя точка ребра принадлежит ровно двум граням, смежным поэтому ребру,
  3) для любой вершины все грани, которым она принадлежит, образуют замкнутую цепочку граней, смежных по ребрам, содержащих эту вершину.

  Опр.Многогранная поверхность называется связной, если для любых двух граней верно следующее: можно перейти от одной грани к другой по цепочке граней, смежных по каким-то ребрам.

  Опр. Многогранником назовем связную вложенную многогранную поверхность вместе с одной из двух компонент (на которые она разбивает пространство), которая ограничена.
  
  Опр. Многогранник называется выпуклым, если множество его точек – выпуклое подмножество в ℝ^3.
  
  Т (Эйлера для выпуклого многогранника)
    V - E + F = 2.

  Опр. Правильный многогранник – многогранник, у которого:
  • все грани – правильные 𝑛𝑛-угольники (одно и то же 𝑛𝑛 для всех граней)
  • все двугранные углы равны.
  
  Т.
    Существует ровно 5 правильных многогранников: тетраэдр, куб, октаэдр, икосаэдр, додекаэдр (платоновы тела).

























  


















