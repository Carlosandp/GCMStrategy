# Experimental Quantum Battle of the Sexes (EQBSCQ)

Un repositorio para implementar y comparar las versiones clásica y cuántica del juego **Battle of the Sexes** bajo el esquema Eisert–Wilkens–Lewenstein (EWL), con énfasis en la **Guided Circuit Mapping Strategy (GCM_Strategy)** para mitigación de errores en hardware NISQ.

---

## 📋 Contenido

- [Descripción](#descripción)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Estructura del Repositorio](#estructura-del-repositorio)
- [Uso](#uso)
  - [Simulación Local (Aer)](#simulación-local-aer)
  - [Ejecución en Hardware Real](#ejecución-en-hardware-real)
  - [Barrido de Parámetros](#barrido-de-parámetros)
- [Metodología](#metodología)
- [Resultados y Visualización](#resultados-y-visualización)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

---

## Descripción

**EQBSCQ** valida experimentalmente el juego *Battle of the Sexes* en dos modalidades:

1. **Clásico:** cálculo del equilibrio de Nash mixto para Alice y Bob como referencia.
2. **Cuántico:** implementación del esquema EWL con:
   - Simulación ideal (Qiskit–Aer).
   - Simulación con ruido (modelo de dispositivo IBM).
   - Ejecución en QPU real de IBM Quantum.

Se exploran 31 valores del parámetro de entrelazamiento γ ∈ [0, π], comparando pagos teóricos, simulados y reales. La **GCM_Strategy** asigna dinámicamente pares de qubits para minimizar la interferencia y mejorar la fidelidad en hardware NISQ.

---

## Requisitos

- Python ≥ 3.8
- Qiskit == 2.0.1
- Qiskit-Aer == 0.17.0
- Qiskit-IBM-Runtime == 0.39.0
- NumPy, Matplotlib, NetworkX

---

## Instalación

```bash
# (Opcional) Crear y activar entorno virtual
env_name="eqbscq_venv"
python -m venv $env_name
source $env_name/bin/activate  # Linux/macOS
# Activate on Windows:
# $env_name\Scripts\activate

# Instalar dependencias
pip install -U -c https://qisk.it/1-0-constraints \
    qiskit==2.0.1 \
    qiskit-aer==0.17.0 \
    qiskit-ibm-runtime==0.39.0 \
    numpy matplotlib networkx
```

---

## Estructura del Repositorio

```
├── README.md               # Documentación principal
├── src/
│   ├── classical/          # Scripts para versión clásica
│   ├── quantum/            # Circuitos EWL y simulaciones
│   ├── gcm_strategy/       # Implementación de GCM_Strategy
│   └── utils/              # Funciones auxiliares
├── notebooks/              # Jupyter Notebooks de análisis
├── data/                   # Resultados crudos y procesados
└── requirements.txt        # Lista de dependencias
```

---

## Uso

### Simulación Local (Aer)

```bash
python src/quantum/run_aer.py \
  --gamma_values 0.0 0.1 ... 3.14 \
  --shots 2048
```

### Ejecución en Hardware Real

```bash
python src/gcm_strategy/execute_qpu.py \
  --backend ibm_sherbrooke \
  --gamma_values 0.0 0.1 ... 3.14 \
  --shots 2048 \
  --use_gcm
```

### Barrido de Parámetros

```bash
python src/utils/parameter_sweep.py \
  --script execute_qpu.py \
  --repetitions 5 \
  --use_gcm
```

---

## Metodología

1. Definición de circuitos EWL parametrizados según γ.
2. Implementación de estrategias locales: I, H, R(π/4), R(π).
3. Aplicación de **GCM_Strategy**: selección dinámica y reasignación iterativa de pares de qubits.
4. Ejecutar simulaciones y experimentos en QPU.
5. Recolección de conteos, cálculo de pagos, ECM e intervalos de confianza.

---

## Resultados y Visualización

- Los notebooks en `notebooks/` muestran la generación de gráficos: pagos vs. γ, ECM y análisis de varianza.
- Los datos procesados se encuentran en `data/processed/`.

---

## Contribuciones

Las aportaciones bienvenidas incluyen:
- Mejora de la **GCM_Strategy**.
- Extensión a otros juegos o arquitecturas cuánticas.
- Integración con frameworks de mitigación de errores.

---

## Licencia

Este proyecto está licenciado bajo MIT License. Véase el archivo `LICENSE` para más detalles.
