�л������ļ���Ҫ����config-server�����������Ķ�ȡ��github��������Ϣ
	http://localhost:8001/neo-config/dev
	���أ�
		{"name":"neo-config","profiles":["dev"],"label":null,"version":"74750593125487fd8bb23697e20637d63fd5cb46","state":null,"propertySources":[{"name":"https://github.com/dewen2018/springcloud/config-repo/neo-config-dev.properties","source":{"neo.hello":"hello im dev update1"}}]}
ֱ�Ӳ鿴�����ļ��е�������Ϣ��
	http://localhost:8001/neo-config-dev.properties
	���أ�
		neo.hello: hello im dev update1
ԭ���ֿ��е������ļ��ᱻת����web�ӿڣ����ʿ��Բ������µĹ���
	/{application}/{profile}[/{label}]
	/{application}-{profile}.yml
	/{label}/{application}-{profile}.yml
	/{application}-{profile}.properties
	/{label}/{application}-{profile}.properties
	��neo-config-dev.propertiesΪ���ӣ�����application��neo-config��profile��dev��client�������д�Ĳ�����ѡ���ȡ��Ӧ�����á�
	
	
����client�����ã�
	spring-cloud��ص����Ա���������bootstrap.properties�У�config�������ݲ��ܱ���ȷ���ء���Ϊconfig��������û�����application.properties����bootstrap.properties�ļ���Ҳ������application.properties��
���⣺��Ϊspringboot��Ŀֻ����������ʱ��Ż��ȡ�����ļ���ֵ���޸�github��Ϣ��client�˲�û���ڴ�ȥ��ȡ�����Ե����������
Spring Cloud Config�ַ���˺Ϳͻ��ˣ�����˸���git��svn���д洢�������ļ�������REST�ӿڣ��ͻ��˿��Դӷ����REST�ӿڻ�ȡ���á����ͻ��˲�����������֪�����õı仯���Ӷ�����ȥ��ȡ�µ����á��ͻ������ȥ������ȡ�µ�������Ϣ�أ�springcloud�Ѿ��������ṩ�˽��������ÿ���ͻ���ͨ��POST�����������Ե�/refresh��
������spring-boot-starter-actuator����spring-boot-starter-actuator��һ�׼�صĹ��ܣ����Լ�س���������ʱ״̬�����оͰ���/refresh�Ĺ��ܡ�