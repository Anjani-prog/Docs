## Repeating elements in code

  inside render method add repeating code 

                 const header = () => {
                            return (
                                <Header backgroundColor='#2383c9'
                                    leftComponent={{
                                        icon: 'arrow-left',
                                        type: 'font-awesome',
                                        color: '#fff',
                                        onPress: () => this.props.navigation.goBack()
                                    }}
                                    centerComponent={{ text: 'Exam Shedule', style: { color: '#fff' } }}
                                />
                            )
                        }


    //  call the code by placing {header()}
    
 ## Header
 ### White square on Header icon press
        <View>
            <Header
              outerContainerStyles={styles.topMenu}
              centerComponent={{
                text: 'Events',
                style: {color: '#fff', fontWeight: 'bold', fontSize: 18}
              }}
              rightComponent={{
                  icon: 'search',
                  color: '#fff',
                  onPress: this.toggleFiltersBox,
                  underlayColor: '#64b5f6' // <-- this does the magic
              }}
            />
        </View>
