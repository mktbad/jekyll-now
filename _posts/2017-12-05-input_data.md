self.data_X = np.empty((0,self.input_height,self.input_width,1), float)
            self.images = glob(os.path.join("./data", self.dataset_name, "*.jpg"))
            for image in self.images:
                self.data_X = np.append(self.data_X, np.array([imread(image).reshape([self.input_height,self.input_width,1])]), axis=0)

def imread(path, grayscale = False):
    if (grayscale):
        return scipy.misc.imread(path, flatten = True).astype(np.float)
    else:
        return scipy.misc.imread(path).astype(np.float)
