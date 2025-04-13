In this repo, only Python was used.

Libraries:
mediapipe
opencv-python
scikit-learn

By landmark detection feature in mediapipe,
the hands will be detected and classified
in real time. Labels have 8 classes:
"A", "B", "L", and numbers from 1 to 5.
The model was trained only on these
hand signs.

Random Forest Classifier model in scikit-learn
was used.




Project workflow is as follows:
- Using opencv, dataset folders was created
manually, hand location and distance to the
camera in each of these classes vary,
which makes the model "robust" to hand size
and hand rotation (I hope).

- Then, using mediapipe, hand landmarks
were detected as coordinates (x, y, z).

- Random Forest model was trained to
classify the inputs. The idea of using
Random forest, instead of CNNs, is that
the inputs are the coordinates x, y, z,
and the output depends on the relative
position of these coordinates. Since
random forest algorithm splits the data
based on that condition of the columns
(which are coordinates in our case),
it seems fairly reasonable to use that
model.

- Then, the model was tested for accuracy,
which was around ~90%. The errors were
because of the similarity of letter "B"
and number "4". 




During inference, hand landmarks are
shown and bounding box is drawn around 
the hand. On top of the bounding box,
the predicted symbol is returned.
