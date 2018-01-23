# PointinTriangle
Point in 2D triangle

Hi, I'd like to know if a point is inside a 2D triangle. I have the following code for android app, but doesn't seem to work:


public class Triangle {
    private float[] v;

    public Triangle(double py1,double px1,double py2, double px2,double py3, double px3)
    {
        v = new float[6];
        v[0] = (float)py1; // Y punto 1
        v[1] = (float)px1; // X punto 1
        v[2] = (float)py2; // Y punto 2
        v[3] = (float)px2; // X punto 2
        v[4] = (float)py3; // Y punto 3
        v[5] = (float)px3; // X punto 3
    }

    private float sign(PointF p1, PointF p2, PointF p3) {
        return (p1.x - p3.x) * (p2.y - p3.y) - (p2.x - p3.x) * (p1.y - p3.y);
    }

    private boolean pointInTriangle(PointF pt, PointF v1, PointF v2, PointF v3) {
        boolean b1, b2, b3;
        b1 = sign(pt, v1, v2) < 0.0f;
        b2 = sign(pt, v2, v3) < 0.0f;
        b3 = sign(pt, v3, v1) < 0.0f;
        return ((b1 == b2) && (b2 == b3));
    }

    public boolean pit(float x, float y) {
        return pointInTriangle(new PointF(x, y), new PointF(v[0], v[1]), new PointF(v[2], v[3]), new PointF(v[4], v[5]));
    }

}
