![[Pasted image 20250313124830.png]]


1. Спарсил все данные узнать сколько RAM/ROM областей внутри .map файла
2. Для каждой области завести структуру 
   struct MemoryObject {
    QString name;
    uint32_t execAddr;
    uint32_t loadAddr;
    uint32_t size;
    uint32_t maxSize;
	 QList <MemoryRegion> memReg;
};
3.  внутри области спарсить все 