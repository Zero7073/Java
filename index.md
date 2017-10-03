public class HashCollection {
	
	
	private Object[] hashValue;
	private Object[] quote;
	private Object[] tail;
	
	public void addd(Object obj) {
		
		if(hashValue == null) {
			
			hashValue = new Object[400];
		}
		
		int index = obj.hashCode() % hashValue.length;
		
		if(index <= -1) {
			
			index = ~index;
		}
		
		if(hashValue[index] == null) {
			
			hashValue[index] = new Object[] {obj, null};
			quote = null;
		}else {
			
			Object[] temporaryObj = new Object[] {obj, null};
			
			if(quote == null ) {
				
				quote = (Object[])hashValue[index];
				quote[1] = temporaryObj;
				tail = temporaryObj;
				
			}else {
				
				tail[1] = temporaryObj;
				tail = temporaryObj;
				
			}
		}
		
	
	}
	
	public boolean judgment(Object obj) {
		
		int index = obj.hashCode() % hashValue.length;
		if(index <= -1) {
			index = ~index;
		}
		
		if(hashValue[index] != null) {
			Object[] quote1 = (Object[])hashValue[index];
			
			while(true) {
				if(quote1 == null) {
					return false;
				}
				
				if(obj.equals(quote1[0])) {
					return true;
				}else {
					quote1 = (Object[])quote1[1];
				}
			}
		}
	return false;
	}
	
	int i=0;
	public void printValue(Object[] obj) {
	Object[] thisObj = obj;
		while(true) {
	    if(thisObj == null) {
	    	break;
	    }else {
	    	
	         System.out.println(thisObj[0]);
	         System.out.println(i++);
	         thisObj = (Object[])thisObj[1];
	  }
	}
}

	int index = 0;
	public void  getValue() {
		
		Object[] value = (Object[])hashValue[index];
		while(true) {
			if(index >= hashValue.length-1) {
				break;
			}
		
			if(value!= null) {
			    printValue(value);
			} 
			index++;
		    value = (Object[])hashValue[index];   
	  }
	    
	}
}

