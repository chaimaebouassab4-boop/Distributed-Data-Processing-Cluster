# Distributed-Data-Processing-Cluster
 Big Data cluster implementation with Hadoop &amp; Spark |  Multi-node distributed architecture (Master/Worker) |  PySpark data processing &amp; Grafana visualization |  Academic Big Data project with 100+ Mo dataset analysis

# 🔥 Big Data Cluster: Hadoop & Spark Implementation

## 📋 Project Overview

Complete **Big Data infrastructure implementation** featuring a distributed **Hadoop/Spark cluster** for large-scale data processing and analysis. This academic project demonstrates the full lifecycle of Big Data engineering: from cluster configuration to distributed storage (HDFS), parallel processing (Spark), and interactive visualization (Grafana).

**Context:** Big Data Architecture & Technologies - Master's Project  
**Team:** GAROUD Fatima Ezzahraa, BOUASSAB Chaimae, ABABRI Chaimae  
**Instructor:** Prof. Anouar Abdelhakim BOUDHIR  
**Institution:** Abdelmalek Essaadi University - Faculty of Sciences and Techniques, Tangier  
**Submission Date:** June 15, 2025

---

## 🎯 Project Objectives

### Phase 1: Cluster Installation & Configuration ✅
- Deploy **Ubuntu Server 22.04** on dedicated hardware (Room E26)
- Configure **Master/Worker architecture** with network isolation
- Install and configure **Hadoop 3.3.6** ecosystem (HDFS, YARN, MapReduce)
- Install and configure **Apache Spark 3.4.2** with PySpark
- Secure cluster with **SSH keys** and **firewall rules** (UFW)

### Phase 2: Distributed Storage & Data Manipulation ✅
- Format and start **HDFS** (Hadoop Distributed File System)
- Ingest large datasets (100+ MB) into HDFS
- Execute **PySpark scripts** for data cleaning and transformation
- Perform distributed operations: `filter`, `groupBy`, `aggregate`, `join`
- Export processed data to **Parquet format** for analytics

### Phase 3: Real-World Case Study - Amazon Product Reviews ✅
- Analyze **Amazon reviews dataset** (7 MB JSON)
- Clean and normalize text data for NLP
- Calculate product statistics (review count, average rating)
- Visualize insights with **Grafana** dashboards (Docker)
- Generate interactive charts: histograms, pie charts, bar graphs

---

## 🏗️ Cluster Architecture

### Distributed Infrastructure Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                    Big Data Cluster                              │
│                   (2-Node Architecture)                          │
└──────────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┴─────────────────────┐
        │                                           │
        ▼                                           ▼
┌────────────────────────┐              ┌────────────────────────┐
│   ubuntumasterfch      │              │   ubuntuworkerfch      │
│   (Master Node)        │◄────SSH─────►│   (Worker Node)        │
│   IP: 192.168.180.49   │              │   IP: 192.168.180.50   │
├────────────────────────┤              ├────────────────────────┤
│ Hadoop Services:       │              │ Hadoop Services:       │
│ ✅ NameNode            │              │ ✅ DataNode            │
│ ✅ ResourceManager     │              │ ✅ NodeManager         │
│ ✅ Secondary NameNode  │              │                        │
│                        │              │ Spark Services:        │
│ Spark Services:        │              │ ✅ Worker Node         │
│ ✅ Master              │              │ ✅ Executors           │
│ ✅ Driver              │              │                        │
│                        │              │ Storage:               │
│ Ports Exposed:         │              │ 📁 Data Blocks         │
│ • HDFS: 9870           │              │ 📦 Local Storage       │
│ • YARN: 8088           │              │                        │
│ • Spark UI: 8080       │              │ Ports:                 │
└────────────────────────┘              │ • DataNode: 9864       │
                                        │ • NodeManager: 8042    │
                                        └────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  HDFS Storage    │
                    │  (Distributed)   │
                    │  • Replication=1 │
                    │  • Block Size=   │
                    │    128MB         │
                    └──────────────────┘
```

### Node Roles & Responsibilities

| Component | Master Node (ubuntumasterfch) | Worker Node (ubuntuworkerfch) |
|-----------|------------------------------|-------------------------------|
| **HDFS** | NameNode (metadata management) | DataNode (block storage) |
| **YARN** | ResourceManager (resource allocation) | NodeManager (task execution) |
| **Spark** | Master + Driver (job orchestration) | Worker + Executors (computation) |
| **OS** | Ubuntu Server 22.04 | Ubuntu Server 22.04 |
| **Java** | OpenJDK 11 | OpenJDK 11 |
| **Network** | Static IP: 192.168.180.49 | Static IP: 192.168.180.50 |

---

## 🛠️ Technology Stack

### Core Components

| Technology | Version | Purpose |
|------------|---------|---------|
| **Apache Hadoop** | 3.3.6 | Distributed storage (HDFS) & resource management (YARN) |
| **Apache Spark** | 3.4.2 | Distributed data processing & analytics |
| **PySpark** | 3.4.2 | Python API for Spark |
| **Java (OpenJDK)** | 11 | Runtime environment for Hadoop/Spark |
| **Ubuntu Server** | 22.04 LTS | Operating system |
| **Grafana** | Latest (Docker) | Data visualization & dashboards |
| **Docker** | 24.x | Container runtime for Grafana |

### Data Formats
- **Input:** JSON (Amazon reviews), CSV
- **Processing:** RDD, DataFrame (Spark)
- **Output:** Parquet (columnar storage)

---

## 📁 Repository Structure

```
📁 Hadoop-Spark-BigData-Cluster/
├── README.md                              # This file
├── docs/
│   ├── projet_final_report.pdf            # Complete project report (45 pages)
│   ├── architecture-diagram.png           # Cluster architecture schema
│   ├── installation-log.md                # Installation journal
│   └── screenshots/
│       ├── hdfs-web-ui.png
│       ├── yarn-dashboard.png
│       ├── spark-job-execution.png
│       └── grafana-visualizations.png
│
├── phase1-installation/                   # Phase 1: Cluster Setup
│   ├── master-node/
│   │   ├── 01-create-hadoop-user.sh       # User creation script
│   │   ├── 02-configure-ssh.sh            # SSH key generation
│   │   ├── 03-network-setup.sh            # Static IP configuration
│   │   ├── 04-install-java.sh             # OpenJDK 11 installation
│   │   ├── 05-install-hadoop.sh           # Hadoop installation
│   │   └── 06-install-spark.sh            # Spark installation
│   ├── worker-node/
│   │   ├── 01-setup-worker.sh             # Worker initialization
│   │   ├── 02-hadoop-config.sh            # Hadoop configuration
│   │   └── 03-spark-config.sh             # Spark configuration
│   └── configs/
│       ├── core-site.xml                  # Hadoop core configuration
│       ├── hdfs-site.xml                  # HDFS configuration
│       ├── yarn-site.xml                  # YARN configuration
│       ├── mapred-site.xml                # MapReduce configuration
│       ├── spark-env.sh                   # Spark environment
│       └── workers                        # Worker nodes list
│
├── phase2-data-manipulation/              # Phase 2: HDFS & Spark
│   ├── hdfs-scripts/
│   │   ├── format-namenode.sh             # HDFS formatting
│   │   ├── start-services.sh              # Start HDFS/YARN
│   │   ├── create-directories.sh          # Create HDFS folders
│   │   └── upload-data.sh                 # Upload CSV/JSON to HDFS
│   ├── spark-scripts/
│   │   ├── json_cleaning.py               # PySpark data cleaning
│   │   ├── product_analysis.py            # Product statistics
│   │   ├── text_preprocessing.py          # NLP text normalization
│   │   └── save_to_parquet.py             # Export to Parquet
│   └── sample-data/
│       ├── mental_disorders_reddit.csv    # Sample CSV data
│       └── DataProduct.json               # Amazon reviews (7 MB)
│
├── phase3-analysis-visualization/         # Phase 3: Analytics
│   ├── notebooks/
│   │   ├── exploratory_analysis.ipynb     # Jupyter notebook
│   │   └── product_insights.ipynb         # Statistical analysis
│   ├── processed-data/
│   │   ├── cleaned_reviews_parquet/       # Cleaned reviews
│   │   └── product_stats_parquet/         # Aggregated stats
│   ├── grafana/
│   │   ├── docker-compose.yml             # Grafana deployment
│   │   ├── dashboards/
│   │   │   ├── product-overview.json
│   │   │   └── review-analytics.json
│   │   └── infinity-datasource-config.json
│   └── visualizations/
│       ├── age-salary-barchart.png
│       ├── salary-histogram.png
│       └── distribution-piechart.png
│
└── scripts/
    ├── full-cluster-deploy.sh             # Automated full deployment
    ├── cluster-health-check.sh            # Cluster status verification
    ├── stop-all-services.sh               # Graceful shutdown
    └── troubleshooting.sh                 # Common issue fixes
```

---

## 🚀 Installation Guide (Phase 1)

### Prerequisites

**Hardware Requirements (per node):**
- **CPU:** 2+ cores (4 cores recommended)
- **RAM:** 4 GB minimum (8 GB recommended)
- **Storage:** 50 GB minimum (100 GB recommended)
- **Network:** Gigabit Ethernet

**Software Requirements:**
- Ubuntu Server 22.04 LTS (minimal installation)
- Root access (sudo privileges)
- Internet connection for package downloads

---

### Master Node Setup (ubuntumasterfch)

#### Step 1: Create Hadoop User

```bash
# Create dedicated user for Hadoop/Spark
sudo adduser hadoopuser --disabled-password --gecos ""

# Add to sudo group
sudo usermod -aG sudo hadoopuser

# Switch to hadoop user
su - hadoopuser
```

#### Step 2: Configure SSH (passwordless authentication)

```bash
# Generate SSH key pair
ssh-keygen -t rsa -P "" -f ~/.ssh/id_rsa

# Authorize key for local login
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

# Test SSH
ssh localhost
# Should connect without password prompt
```

#### Step 3: Configure Network

**Set hostname:**
```bash
sudo hostnamectl set-hostname ubuntumasterfch
```

**Configure `/etc/hosts`:**
```bash
sudo nano /etc/hosts

# Add these lines:
192.168.180.49    ubuntumasterfch master
192.168.180.50    ubuntuworkerfch worker
```

**Set static IP (Netplan):**
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

**Content:**
```yaml
network:
  version: 2
  ethernets:
    enp0s3:  # Replace with your interface name
      dhcp4: no
      addresses:
        - 192.168.180.49/24
      gateway4: 192.168.180.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
```

**Apply configuration:**
```bash
sudo netplan apply

# Verify
ip addr show enp0s3
ping -c 4 google.com
```

#### Step 4: Configure Firewall

```bash
# Install UFW
sudo apt update
sudo apt install ufw -y

# Allow essential ports
sudo ufw allow 22/tcp        # SSH
sudo ufw allow 9870/tcp      # HDFS NameNode Web UI
sudo ufw allow 8088/tcp      # YARN ResourceManager Web UI
sudo ufw allow 8080/tcp      # Spark Master Web UI
sudo ufw allow 9000/tcp      # HDFS NameNode IPC
sudo ufw allow 8020/tcp      # HDFS NameNode IPC (alternative)

# Enable firewall
sudo ufw enable

# Verify
sudo ufw status verbose
```

#### Step 5: Install Java (OpenJDK 11)

```bash
# Install OpenJDK 11
sudo apt update
sudo apt install openjdk-11-jdk -y

# Verify installation
java -version
# Output: openjdk version "11.0.x"

# Configure JAVA_HOME
echo 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc

# Verify
echo $JAVA_HOME
```

#### Step 6: Install Hadoop 3.3.6

```bash
# Download Hadoop
cd /tmp
wget https://downloads.apache.org/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz

# Extract to /usr/local
sudo tar -xzf hadoop-3.3.6.tar.gz -C /usr/local/
sudo mv /usr/local/hadoop-3.3.6 /usr/local/hadoop

# Set ownership
sudo chown -R hadoopuser:hadoopuser /usr/local/hadoop

# Configure environment variables
cat >> ~/.bashrc << 'EOF'
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
EOF

source ~/.bashrc

# Verify
hadoop version
# Output: Hadoop 3.3.6
```

**Configure Hadoop:**

**1. Edit `core-site.xml`:**
```bash
nano $HADOOP_HOME/etc/hadoop/core-site.xml
```

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://ubuntumasterfch:9000</value>
  </property>
  <property>
    <name>hadoop.tmp.dir</name>
    <value>/home/hadoopuser/hadoopdata/tmp</value>
  </property>
</configuration>
```

**2. Edit `hdfs-site.xml`:**
```xml
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>1</value>
  </property>
  <property>
    <name>dfs.namenode.name.dir</name>
    <value>/home/hadoopuser/hadoopdata/namenode</value>
  </property>
  <property>
    <name>dfs.datanode.data.dir</name>
    <value>/home/hadoopuser/hadoopdata/datanode</value>
  </property>
  <property>
    <name>dfs.namenode.http-address</name>
    <value>ubuntumasterfch:9870</value>
  </property>
</configuration>
```

**3. Edit `yarn-site.xml`:**
```xml
<configuration>
  <property>
    <name>yarn.resourcemanager.hostname</name>
    <value>ubuntumasterfch</value>
  </property>
  <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
  </property>
  <property>
    <name>yarn.resourcemanager.webapp.address</name>
    <value>ubuntumasterfch:8088</value>
  </property>
</configuration>
```

**4. Edit `mapred-site.xml`:**
```xml
<configuration>
  <property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
  </property>
</configuration>
```

**5. Edit `workers` file:**
```bash
echo "ubuntuworkerfch" > $HADOOP_HOME/etc/hadoop/workers
```

**6. Create HDFS directories:**
```bash
mkdir -p /home/hadoopuser/hadoopdata/{namenode,datanode,tmp}
chmod 755 /home/hadoopuser/hadoopdata
```

#### Step 7: Install Spark 3.4.2

```bash
# Download Spark
cd /tmp
wget https://downloads.apache.org/spark/spark-3.4.2/spark-3.4.2-bin-hadoop3.tgz

# Extract
sudo tar -xzf spark-3.4.2-bin-hadoop3.tgz -C /usr/local/
sudo mv /usr/local/spark-3.4.2-bin-hadoop3 /usr/local/spark

# Set ownership
sudo chown -R hadoopuser:hadoopuser /usr/local/spark

# Configure environment
cat >> ~/.bashrc << 'EOF'
export SPARK_HOME=/usr/local/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
export PYSPARK_PYTHON=/usr/bin/python3
EOF

source ~/.bashrc

# Verify
spark-shell --version
# Output: version 3.4.2
```

**Configure Spark:**

**1. Create `spark-env.sh`:**
```bash
cp $SPARK_HOME/conf/spark-env.sh.template $SPARK_HOME/conf/spark-env.sh
nano $SPARK_HOME/conf/spark-env.sh
```

**Add:**
```bash
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
export SPARK_MASTER_HOST=ubuntumasterfch
export SPARK_MASTER_PORT=7077
```

**2. Configure workers:**
```bash
echo "ubuntuworkerfch" > $SPARK_HOME/conf/workers
```

---

### Worker Node Setup (ubuntuworkerfch)

#### Quick Setup Script

```bash
# 1. Create hadoopuser (same as master)
sudo adduser hadoopuser --disabled-password --gecos ""
sudo usermod -aG sudo hadoopuser

# 2. Copy SSH public key from master
# On master:
ssh-copy-id hadoopuser@ubuntuworkerfch

# 3. Configure hostname and /etc/hosts (same as master)
sudo hostnamectl set-hostname ubuntuworkerfch

sudo nano /etc/hosts
# Add:
# 192.168.180.49    ubuntumasterfch master
# 192.168.180.50    ubuntuworkerfch worker

# 4. Set static IP (192.168.180.50)

# 5. Install Java, Hadoop, Spark (same versions as master)
# Copy configuration files from master:
scp -r hadoopuser@ubuntumasterfch:/usr/local/hadoop /usr/local/
scp -r hadoopuser@ubuntumasterfch:/usr/local/spark /usr/local/

# 6. Create HDFS directories
mkdir -p /home/hadoopuser/hadoopdata/datanode
```

---

## 📊 Phase 2: Data Manipulation

### Start Hadoop Services

```bash
# On Master Node (ubuntumasterfch)

# 1. Format NameNode (FIRST TIME ONLY)
hdfs namenode -format

# 2. Start HDFS
start-dfs.sh

# 3. Start YARN
start-yarn.sh

# 4. Verify services
jps
# Output:
# NameNode
# SecondaryNameNode
# ResourceManager

# On Worker Node (check):
jps
# Output:
# DataNode
# NodeManager
```

**Access Web UIs:**
- **HDFS NameNode:** http://192.168.180.49:9870
- **YARN ResourceManager:** http://192.168.180.49:8088

---

### Upload Data to HDFS

```bash
# Create HDFS directories
hdfs dfs -mkdir -p /user/hadoopuser
hdfs dfs -mkdir /data

# Upload JSON file (7 MB)
hdfs dfs -put DataProduct.json /data/

# Verify
hdfs dfs -ls /data
# Output:
# -rw-r--r--   1 hadoopuser supergroup    7340032 2025-05-15 10:30 /data/DataProduct.json

# Check HDFS storage
hdfs dfsadmin -report
```

---

### PySpark Data Processing

**Script: `json_cleaning.py`**

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, regexp_replace, length, avg, count

# Initialize Spark Session
spark = SparkSession.builder \
    .appName("Amazon Reviews Cleaning") \
    .master("spark://ubuntumasterfch:7077") \
    .getOrCreate()

# Read JSON from HDFS
df = spark.read.json("hdfs://ubuntumasterfch:9000/data/DataProduct.json")

# Display schema
df.printSchema()

# Data Cleaning
# 1. Clean reviewText (remove non-alphabetic characters)
df_clean = df.withColumn(
    "clean_text",
    regexp_replace(col("reviewText"), "[^a-zA-Z\\s]", "")
)

# 2. Calculate text length
df_clean = df_clean.withColumn("text_length", length("clean_text"))

# 3. Filter out short reviews (< 50 characters)
df_filtered = df_clean.filter(col("text_length") >= 50)

# 4. Remove duplicates
df_deduplicated = df_filtered.dropDuplicates(["reviewerID", "asin"])

# Show sample
df_deduplicated.select("asin", "overall", "clean_text", "text_length").show(10, truncate=50)

# Aggregate Statistics by Product
product_stats = df_deduplicated.groupBy("asin").agg(
    count("*").alias("nb_reviews"),
    avg("overall").alias("avg_rating")
)

# Sort by review count
product_stats_sorted = product_stats.orderBy(col("nb_reviews").desc())
product_stats_sorted.show(10)

# Join: Enrich each review with product stats
df_enriched = df_deduplicated.join(product_stats, on="asin", how="left")

# Show joined data
df_enriched.select("asin", "text_length", "nb_reviews", "avg_rating").show(10)

# Save to Parquet (compressed, columnar format)
df_enriched.write.mode("overwrite").parquet(
    "hdfs://ubuntumasterfch:9000/processed/cleaned_reviews_parquet"
)

product_stats_sorted.write.mode("overwrite").parquet(
    "hdfs://ubuntumasterfch:9000/processed/product_stats_parquet"
)

print("✅ Data processing completed successfully!")
print("📂 Output saved to: /processed/cleaned_reviews_parquet")
print("📂 Stats saved to: /processed/product_stats_parquet")

spark.stop()
```

**Run the script:**
```bash
# Submit to Spark cluster
spark-submit --master spark://ubuntumasterfch:7077 json_cleaning.py

# Monitor job progress in Spark UI:
# http://192.168.180.49:8080
```

**Results:**

| asin | text_length | nb_reviews | avg_rating |
|------|-------------|------------|------------|
| B003VWJ2K8 | 261 | 162 | 4.685 |
| B0002E1G5C | 227 | 142 | 4.577 |
| 1384719342 | 315 | 5 | 5.0 |

---

## 📈 Phase 3: Visualization with Grafana

### Setup Grafana (Docker)

```bash
# On your local machine (Windows/Mac/Linux)

# Create docker-compose.yml
cat > docker-compose.yml << 'EOF'
version: '3.8'

services:
  grafana:
    image: grafana/grafana:latest
    container_name: grafana-bigdata
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=admin
      - GF_INSTALL_PLUGINS=yesoreyeram-infinity-datasource
    volumes:
      - grafana-storage:/var/lib/grafana
    restart: always

volumes:
  grafana-storage:
EOF

# Start Grafana
docker-compose up -d

# Access Grafana
# http://localhost:3000
# Login: admin / admin
```

### Install Infinity Data Source Plugin

1. Navigate to **Configuration** → **Plugins**
2. Search for **"Infinity"**
3. Click **Install**
4. Restart Grafana container: `docker-compose restart`

---

### Export Data from HDFS

```bash
# On Master Node: Export Parquet to CSV
spark-submit --master local[*] << 'EOF'
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("Export to CSV").getOrCreate()

# Read Parquet
df = spark.read.parquet("hdfs://ubuntumasterfch:9000/processed/product_stats_parquet")

# Save as single CSV
df.coalesce(1).write.mode("overwrite").option("header", "true").csv("/tmp/product_stats_csv")

spark.stop()
EOF

# Download CSV to local machine
scp hadoopuser@192.168.180.49:/tmp/product_stats_csv/*.csv ./product_stats.csv
```

---

### Create Grafana Dashboard

1. **Add Infinity Data Source:**
   - Go to **Configuration** → **Data Sources**
   - Add **Infinity**
   - Choose **CSV** as type
   - Upload `product_stats.csv`

2. **Create Panels:**

**Panel 1: Top 10 Products by Review Count**
- Type: **Bar Chart**
- Query: `SELECT asin, nb_reviews FROM infinity WHERE nb_reviews > 50 ORDER BY nb_reviews DESC LIMIT 10`

**Panel 2: Average Rating Distribution**
- Type: **Histogram**
- Query: `SELECT avg_rating, COUNT(*) FROM infinity GROUP BY avg_rating`

**Panel 3: Review Count Pie Chart**
- Type: **Pie Chart**
- Query: `SELECT asin, nb_reviews FROM infinity LIMIT 10`

---

## 🧪 Testing & Validation

### Cluster Health Check

```bash
# Verify HDFS
hdfs dfsadmin -report

# Verify YARN
yarn node -list

# Verify Spark Workers
$SPARK_HOME/sbin/spark-class org.apache.spark.deploy.Client spark://ubuntumasterfch:7077 list
```

### Performance Metrics

| Metric | Value | Notes |
|--------|-------|-------|
| **Dataset Size** | 7 MB (JSON) | Amazon reviews |
| **HDFS Block Size** | 128 MB | Default |
| **Replication Factor** | 1 | Single worker |
| **Spark Executors** | 1 | Worker node |
| **Processing Time** | ~45 seconds | 7 MB JSON → Parquet |
| **Output Size** | 2.3 MB (Parquet) | 67% compression |
| **Records Processed** | 10,000+ reviews | After filtering |

---

## 🎓 Skills Demonstrated

### Big Data Engineering
- ✅ Multi-node cluster architecture design
- ✅ Distributed storage with HDFS
- ✅ Resource management with YARN
- ✅ Fault tolerance and data replication

### Apache Spark Proficiency
- ✅ PySpark DataFrame API
- ✅ Distributed transformations (`map`, `filter`, `groupBy`)
- ✅ Aggregations and joins
- ✅ Parquet columnar storage optimization

### DevOps & Infrastructure
- ✅ Linux server administration (Ubuntu)
- ✅ SSH key management
- ✅ Network configuration (static IPs, DNS)
- ✅ Firewall rules (UFW)

### Data Visualization
- ✅ Grafana dashboard creation
- ✅ Docker containerization
- ✅ Interactive charts (bar, histogram, pie)

---

## 🔧 Troubleshooting

### Issue: DataNode not starting on Worker

**Diagnosis:**
```bash
# Check logs
tail -f $HADOOP_HOME/logs/hadoop-hadoopuser-datanode-*.log
```

**Common causes:**
1. **Incompatible cluster IDs**
   ```bash
   # On Worker: Delete old data and reformat
   rm -rf /home/hadoopuser/hadoopdata/datanode/*
   # Restart DataNode
   hdfs --daemon start datanode
   ```

2. **Firewall blocking ports**
   ```bash
   sudo ufw allow from 192.168.180.49 to any port 9
