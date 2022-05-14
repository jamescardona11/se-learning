# Tipos de Flow

este [video](https://www.youtube.com/watch?v=M_3VeKPFi5U&list=PLZVwXPbHD1KM5oLAmhz-HHRIMhaOEXku5)

# 1 Git Flow

Simplemente, se van creando feature desde una rama long-term y se van integrando a develop o master
Entonces se van creando features y features

Master, develop, release
Features, hotfix

Desarrollo: Features branches
Pre-prod: Develop
Prod: Releases branches

El estado de algunos hotfix a veces no es consistente porque no se integran.

# 2 Github Flow

Es muy simple.
Solo se tienen dos ramas master y features
Lo que deployean es las ramas features.
Se integra a master es después de que se pasó pruebas

Desarrollo: Features branches
Pre-prod: features
Prod: Features o master

Se entregan más funcionalidades más rapidas.
Master es deployable siempre

# 3 Git release Flow: Microsoft Git

Partimos de master
Tenemos es topic branches (no features)
Se integran los topic a releases
Se deployean releases

Desarrollo: topic branches
Pre-prod: features
Prod: Features o master

Si hay fallos se hace una rama hot fix y cherry-pick para integrrar

# 4 Gitlab flow

Tenemos master se deployea desde staging
Tenemos feature/hotfix y hacemos merge-request para integrar a master
Tenemos diferentes entornos pre-prod y producción que parten desde master

Se usan cherry-picks para hotfix

# 5 Trunk-Based-Development

Master
features branches
Se integan las features a master y se deployean por medio de una rama llamada release branch

Desarrollo: features
Prod: master o Tag

-> Puede tener releases branches
-> Puede tener tags
-> Master siempre es deployable

# 6 Master-only flow / Single branch

Solo tenemos master

Debe ser código de calidad y con buenos test

# Conclusiones:

- Gitlab flow: No gusta, que haya una rama por entorno, agrega complejidad.
  Las build son 'inmutables'
- Release flow: No gusta, porque se espera mucho para hacer deploy.
- Git flow: No, permite con poca inversión de tiempo se aprenda.
  Pero se empieza a complicar la integración de ramas
  Si tenemos test y aumentamos la confianza para que se requiere pre-prod
- Trunk-based develoment: Si, se puede integrar rápido con master y se va deployment
- Github flow: Si, se pueden los entornos dinámicos por features. Se debe tener mucho CI/CD
- Master-only-flow: Si, simplificar para poder entregar más valor.
