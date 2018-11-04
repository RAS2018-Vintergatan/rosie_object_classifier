import roslib
import sys
import rospy
import cv2
from std_msgs.msg import String
from cv_bridge import CvBridge, CvBridgeError

class image_classifier:
	def __init__(self):
		self.object_pub = rospy.Publisher("/Object_ID", String)
		self.bridge = CvBridge()
		self.image_sub = rospy.Subscriber("/camera/rgb/rect_color", Image, self.callback)
	
	def callback(self, data):
		try:
			cv_image = self.bridge.imgmsg_to_cv2(data)
		except CvBridgeError as e:
			print(e)
		cv2.imshow("Image_Window", cv_image)

def main(args):
	ic = image_classifier()
	rospy.init_node('rosie_object_classifier', anonymous = True)
	try:
		rospy.spin()
	except KeyboardInterrupt:
		print("Node shutting down")
	cv2.destroyAllWindows()




