# 🧠 Proyecto: Integración de Kafka y Spark Streaming  
**Autor:** Juan Daniel Coronel Ricaurte
**Curso:** Big Data – UNAD 2025  
**Anexo 3:** Spark Streaming y Kafka  

---

## 📘 Introducción  
Este proyecto corresponde al desarrollo del **Anexo 3: Spark Streaming y Kafka**, cuyo propósito fue implementar un flujo de datos en tiempo real utilizando **Apache Kafka** como plataforma de mensajería y **Apache Spark Streaming** como motor de procesamiento.  
El objetivo principal fue demostrar cómo ambas herramientas trabajan de forma integrada para procesar grandes volúmenes de datos en tiempo real, cumpliendo con el **RAC 2 del curso**: diseñar e implementar soluciones de almacenamiento y procesamiento de grandes volúmenes de datos con Hadoop, Spark y Kafka.

---

## 🎯 Objetivos  

### **Objetivo general**  
Diseñar e implementar una solución de procesamiento de datos en tiempo real utilizando Apache Kafka y Spark Streaming.

### **Objetivos específicos**
1. Configurar e iniciar los servicios de Kafka y ZooKeeper.  
2. Desarrollar un productor en Python para generar datos simulados de sensores.  
3. Implementar un consumidor con Spark Streaming para procesar y analizar los datos en tiempo real.  
4. Validar la conexión y el flujo de datos entre Kafka y Spark.  
5. Documentar el proceso y compartir el código en un repositorio GitHub.

---

## ⚙️ Requisitos previos  
- **Java 17 o superior**  
- **Python 3.10+**  
- **Apache Kafka 3.6.2**  
  > [Descarga desde Apache Archive](https://archive.apache.org/dist/kafka/3.6.2/kafka-3.6.2-src.tgz)  
- **Apache Spark 3.5.6 (con Hadoop 3)**  
  > [Descarga oficial](https://archive.apache.org/dist/spark/spark-3.5.6/spark-3.5.6-bin-hadoop3.tgz)  
- Librerías de Python necesarias:  
  ```bash
  pip install kafka-python pyspark
  ```

---

## 🧩 Estructura del repositorio
```
├── kafka_producer.py              # Script productor: genera datos de sensores
├── spark_streaming_consumer.py    # Script consumidor: procesa los datos en Spark
├── README.md                      # Documento de descripción e instrucciones
```

---

## 🚀 Instrucciones de ejecución

### 1️⃣ Iniciar los servicios
```bash
sudo /opt/Kafka/bin/zookeeper-server-start.sh -daemon /opt/Kafka/config/zookeeper.properties
sudo /opt/Kafka/bin/kafka-server-start.sh -daemon /opt/Kafka/config/server.properties
```

### 2️⃣ Crear el topic
```bash
/opt/Kafka/bin/kafka-topics.sh --create \
  --bootstrap-server localhost:9092 \
  --replication-factor 1 \
  --partitions 1 \
  --topic sensor_data
```

### 3️⃣ Ejecutar el productor
```bash
python3 kafka_producer.py
```

### 4️⃣ Ejecutar el consumidor en Spark Streaming
```bash
python3 spark_streaming_consumer.py
```

---

## 🧠 Solución de errores
- **Error:** `NoBrokersAvailable`  
  ✅ **Solución:** iniciar los servicios de ZooKeeper y Kafka antes de ejecutar el productor.
- **Error:** `Failed to find data source: kafka`  
  ✅ **Solución:** iniciar PySpark con el paquete Kafka.  
  ```bash
  $SPARK_HOME/bin/pyspark --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.5.6
  ```

---

## 📊 Resultados
- El **productor** envía datos simulados de sensores (ID, temperatura, humedad, timestamp).  
- El **consumidor** procesa y agrupa los datos en tiempo real, mostrando estadísticas por minuto.  
- Se validó la conectividad entre Kafka y Spark, confirmando el flujo completo de datos.  

---

## 🎥 Video demostrativo  
> 🎬 *Enlace al video explicativo en YouTube o Google Drive*
> https://drive.google.com/file/d/1xMrzMlhk5fhUxdBIrw9rdMtWaAGSNlKi/view?usp=sharing

