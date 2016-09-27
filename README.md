# hadoop_map_reduce_using_python
This is a very simple example to use python scripts as mappers and reducers for Hadoop MapReduce

## Steps to run

1. find the hadoop streaming jar file in your system

  $> find / -name hadoop-streaming-*.jar

2. set a variable to the jar file (Use your path. This example is my path!)

  $> export STREAMING_JAR=/opt/hadoop-2.7.3/share/hadoop/tools/lib/hadoop-streaming-2.7.3.jar
  
3. download a sample input

  $> wget http://www.gutenberg.org/ebooks/44604.txt.utf-8
  
4. Create input/output directories in HDFS file system. Copy the input file into the input path.

  $> hdfs dfs -mkdir /inputs
  
  $> hdfs dfs -mkdir /outputs
  
  $> hdfs dfs -put /home/work/mapreduce/44604.txt.utf-8 /inputs/
  
5. Run the Mapreduce on YARN using the py scripts as mapper and reducer.

  $> yarn jar $STREAMING_JAR \
    -input /inputs/44604.txt.utf-8 \
    -output /outputs/1 \
    -mapper mapper.py \
    -reducer reducer.py \
    -file /home/work/mapreduce/mapper.py \
    -file /home/work/mapreduce/reducer.py


###Credit : https://www.princeton.edu/researchcomputing/computational-hardware/hadoop/mapred-tut/
