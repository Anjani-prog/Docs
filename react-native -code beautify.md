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
