from PIL import Image
import turtle


def pathMaker(pathDis, degree):
    pathWay.forward(pathDis) # put in forward() function after sleep/ function. pathdis is either 100/0
    pathWay.left(degree) # put in turn functions, degree can either be 90/ -90, 90 when turning left, and -90 when turning right
    return (pathWay.xcor(), pathWay.ycor())

#setup
pathWay = turtle.Turtle()
pathWay.width(10)
pathWay.pencolor("green")
pathWay.left(90)
#end setup

#sample
coor = list([]) #you need an array to store all the value
for i in range(2):
    for a in range(2):
        coor.append(pathMaker(100, 90))
coor.append (pathMaker(40, -90))
coor.append (pathMaker(100, 90))
coor.append (pathMaker(100, -90))

coor.append(pathMaker(100,90))
coor.append(pathMaker(200,0))
print(coor)

#sampleEnd

#2nd Part
#sort
def getExtremeVal(arr, stringInf, index): #arr = array with coordinates, stringInf = "inf" if looking for smallest value, 
    extrCoor = float(stringInf)          #"-inf" if looking for largest value; index = 0, if largest/smallest val for x coordinates 
    for i in range(len(arr)):
        if stringInf == "inf":           # index = 1 if largest/smallest val for y coordinates
            if arr[i][index] <= extrCoor:
                extrCoor = arr[i][index]
        else:
            if arr[i][index] >= extrCoor:
                extrCoor = arr[i][index]
    return extrCoor

#established largest and smallest vals in abs val
x1 = abs( (getExtremeVal(coor, "-inf", 0)) ) #-> largest num in array base on x coordinates
x2 = abs( (getExtremeVal(coor, "inf", 0)) ) #-> smallest num based on x coors
y1 = abs( (getExtremeVal(coor, "-inf", 1)) ) #-> largest num based on y coors
y2 = abs( (getExtremeVal(coor, "inf", 1)) ) #-> smallest num based on y coor

gameBk = Image.new("RGB",(2 * int(x1+x2) + 20, 2* int(y1+y2)+ 20) , (0,0,0))
#compare which abs vals are bigger
def compareVal(a,b):
    if a >= b:
        return a
    else:
        return b
    
def transPathtoPic(im, arr):
    #connect the dots
    newArr = list([])
    for i in range(len(arr)):
        newCoor = (int(arr[i][0] + compareVal(x1, x2)), int(arr[i][1] + compareVal(y1,y2)))
        newArr.append(newCoor)
        print(newArr)
    try:                    
        for count in range(len(newArr)):
            if newArr[count][1] != newArr[count+1][1]:  #change in y
                if newArr[count][1] > newArr[count+1][1]:
                    # if going down
                    a = newArr[count][1] - newArr[count+1][1]
                    for c in range(a):
                        for i in range(10):
                            im.putpixel((newArr[count][0] + i, newArr[count][1] - c), (0,255,0))
                else:
                    #going up
                    a = newArr[count+1][1] - newArr[count][1]
                    for c in range(a):
                        for i in range(10):
                            im.putpixel((newArr[count][0] + i, newArr[count][1] + c), (0,255,0))
            elif newArr[count][0] != newArr[count+1][0]:
                #change in x
                if newArr[count][0] > newArr[count+1][0]:
                    # if going left 
                    a = newArr[count][0] - newArr[count+1][0]
                    for c in range(a):
                        for i in range(10):
                            im.putpixel((newArr[count][0] - c, newArr[count][1] + i), (0,255,0))
                    c = c + 1
                else:
                    #if going right
                    a = newArr[count+1][0] - newArr[count][0]
                    for c in range(a):
                        for i in range(10):
                            im.putpixel((newArr[count][0] + c, newArr[count][1] + i), (0,255,0))
    except:
        pass
    
    return im

gameMap = transPathtoPic(gameBk, coor)
gameMap.show()
gameMap.save("gameMap.jpg")
