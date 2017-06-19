public class LockTest {
    public static void main(String[] args){        LockThread t1 = new LockThread("A");        LockThread t2 = new LockThread("B");        t1.start();        t2.start();    }}
class LockThread extends Thread{    public static final ReentrantLock rlA = new ReentrantLock();    public static final ReentrantLock rlB = new ReentrantLock();    public LockThread(String label){        super();        if ("A".equals(label)) rlA.lock();    }    @Override    public void run() {        if (rlA.isLocked()) rlB.lock();        else rlA.lock();    }}
